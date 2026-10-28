# Google Sheet Email Summary Automation (n8n)

An automated n8n workflow that reads student or participant records from a Google Sheet, validates row data, composes personalized course summaries, and dispatches dynamic emails via Gmail.

---

## 📌 Workflow Overview

```
[Manual / Scheduled Trigger]
             │
             ▼
   [Google Sheets Node] (Fetch rows)
             │
             ▼
        [If Node] (Validate Name != empty)
             │
             ▼
    [Edit Fields (Set)] (Construct Subject & Body)
             │
             ▼
       [Gmail Node] (Send individual emails)
```

1. **Trigger**: Initiates the workflow manually (or can be configured with a Cron trigger for scheduled batches).
2. **Google Sheets (`Get row(s) in sheet`)**: Reads rows from the target Google Sheet (`Sheet1`).
3. **If Filter (`If`)**: Filters out empty rows by validating that the `Name` field is not empty.
4. **Data Formatting (`Edit Fields`)**: Dynamically constructs:
   - `email_subject`: `Data Summary: <Name> - <Course>`
   - `email_body`: Personalized text summary containing Name, Course, Status, Email, and Remarks.
5. **Gmail Delivery (`Send a message`)**: Automatically dispatches the generated message to the recipient's email address extracted from the sheet.

---

## 📋 Prerequisites

Before importing and running the workflow, make sure you have:

1. An active [n8n](https://n8n.io/) instance (self-hosted or n8n Cloud).
2. A **Google Sheets OAuth2** credential configured in n8n.
3. A **Gmail OAuth2** credential configured in n8n.
4. A Google Sheet with the following headers:
   - `Name`
   - `Course`
   - `Status`
   - `Email`
   - `Remarks`

---

## 🚀 Setup & Installation

1. **Import the Workflow**:
   - Open your n8n canvas.
   - Click the **three dots** in the top-right corner -> **Import from File** (or paste the JSON workflow directly).
2. **Configure Credentials**:
   - Open the **Google Sheets** node and select your authenticated Google Sheets credential.
   - Open the **Gmail** node and select your connected Gmail account.
3. **Link Your Sheet**:
   - In the Google Sheets node, choose your spreadsheet from Google Drive or supply your own Document ID and Sheet name.
4. **Test & Execute**:
   - Click **Execute workflow** to process rows and verify sent emails.

---

## ⚙️ Workflow Details

| Node | Type | Purpose |
| :--- | :--- | :--- |
| **When clicking ‘Execute workflow’** | `manualTrigger` | Manual trigger for ad-hoc execution |
| **Get row(s) in sheet** | `googleSheets` | Fetches student/course records |
| **If** | `if` | Drops empty rows lacking a `Name` |
| **Edit Fields** | `set` | Prepares formatted email subject & message body |
| **Send a message** | `gmail` | Sends text email to `$json.Email` |

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).