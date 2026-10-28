{
  "name": "Google Sheet Email Summary",
  "nodes": [
    {
      "parameters": {},
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [
        0,
        0
      ],
      "id": "b3494b9b-717d-49cd-931c-19d54516a1b7",
      "name": "When clicking ‘Execute workflow’"
    },
    {
      "parameters": {
        "documentId": {
          "__rl": true,
          "value": "1KqVNpTxGbUqrB8FqxpfbuqzRmkHKcmui9yWNX16vPSI",
          "mode": "list",
          "cachedResultName": "n8n Assignment - Sample Data",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1KqVNpTxGbUqrB8FqxpfbuqzRmkHKcmui9yWNX16vPSI/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Sheet1",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1KqVNpTxGbUqrB8FqxpfbuqzRmkHKcmui9yWNX16vPSI/edit#gid=0"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        224,
        0
      ],
      "id": "06b72548-a58b-4154-b944-80ef92b90fb1",
      "name": "Get row(s) in sheet",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "SdfhfuMzKsjOBx3B",
          "name": "AI ceo"
        }
      }
    },
    {
      "parameters": {
        "conditions": {
          "options": {
            "caseSensitive": true,
            "leftValue": "",
            "typeValidation": "strict",
            "version": 4
          },
          "conditions": [
            {
              "id": "bd8cf3fe-8f71-40ec-bd2b-4c233eedfc9f",
              "leftValue": "={{ $json[\"Name\"] }}",
              "rightValue": "",
              "operator": {
                "type": "string",
                "operation": "notEmpty",
                "singleValue": true
              }
            }
          ],
          "combinator": "and"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.if",
      "typeVersion": 2.4,
      "position": [
        448,
        0
      ],
      "id": "497755d0-7fef-4b03-97e3-bc9b7dbec283",
      "name": "If"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "55e398ac-3d69-46d9-a95f-16318d8d521a",
              "name": "email_subject",
              "value": "={{ 'Data Summary: ' + $json.Name + ' - ' + $json.Course }}",
              "type": "string"
            },
            {
              "id": "121a47ef-b304-4eae-a9d1-0059490e85be",
              "name": "email_body",
              "value": "={{ 'Hello,\\n\\nHere is the course data summary:\\n\\nName: ' + $json.Name + '\\nCourse: ' + $json.Course + '\\nStatus: ' + $json.Status + '\\nEmail: ' + $json.Email + '\\nRemarks: ' + $json.Remarks + '\\n\\nRegards,\\nCourse Administration' }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.5,
      "position": [
        672,
        -96
      ],
      "id": "c6ba7d81-2ba4-4f01-b4b3-0b7a61792dd5",
      "name": "Edit Fields"
    },
    {
      "parameters": {
        "sendTo": "={{ $('If').item.json.Email }}",
        "subject": "={{ $json.email_subject }}",
        "emailType": "text",
        "message": "={{ $json.email_body }}",
        "options": {
          "appendAttribution": false
        }
      },
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 2.2,
      "position": [
        896,
        -96
      ],
      "id": "c7388b68-7c9b-499b-a09c-4354c0a64ce2",
      "name": "Send a message",
      "webhookId": "e78983ee-04c5-43e3-b000-05b2982fca21",
      "credentials": {
        "gmailOAuth2": {
          "id": "riKM3aLyp5eUTqVp",
          "name": "Ajmalaji81 email"
        }
      }
    }
  ],
  "pinData": {},
  "connections": {
    "When clicking ‘Execute workflow’": {
      "main": [
        [
          {
            "node": "Get row(s) in sheet",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Get row(s) in sheet": {
      "main": [
        [
          {
            "node": "If",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "If": {
      "main": [
        [
          {
            "node": "Edit Fields",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Edit Fields": {
      "main": [
        [
          {
            "node": "Send a message",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "active": true,
  "settings": {
    "executionOrder": "v1",
    "binaryMode": "separate"
  },
  "versionId": "5ce8407e-925b-4574-9bfb-2fb3dd9387c2",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "d2db3f6fcc3b0227e453d88db7b1553a645df4a3771c5292607eeea917279274"
  },
  "nodeGroups": [],
  "id": "pokWnXM1Ks06NAfB",
  "tags": []
}