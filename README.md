# n8n Workflows

A collection of automation workflows built with n8n, OpenRouter AI, and Google Sheets.

## Workflows

### Workflow 1 - GitHub API Integration
Fetches public GitHub user/org data using the GitHub REST API.
- **Trigger:** Manual
- **Key Node:** HTTP Request
- **Use Case:** Pull GitHub profile data on demand

### Workflow 2 - Webhook Data Response
Exposes a webhook endpoint that returns structured JSON data.
- **Trigger:** Webhook (GET)
- **Key Nodes:** Set, Respond to Webhook
- **Use Case:** Lightweight custom API endpoint

### Workflow 3 - Custom Code Logic
Runs custom JavaScript inside n8n to generate dynamic data.
- **Trigger:** Manual
- **Key Node:** Code
- **Use Case:** Data transformation and custom logic

### Smart Customer Support Bot
AI-powered support bot that answers customer questions and logs conversations.
- **Trigger:** Webhook (POST)
- **Key Nodes:** HTTP Request (OpenRouter AI), Google Sheets
- **Use Case:** Automated customer support with logging

### Smart Customer Support Bot v2
Upgraded support bot that answers questions AND categorizes issues automatically.
- **Trigger:** Webhook (POST)
- **Key Nodes:** HTTP Request (OpenRouter AI), Code, Google Sheets
- **Categories:** Technical, Billing, General, Account
- **Use Case:** Smart support routing and ticket categorization

## Setup

1. Import any `.json` file from the `workflows/` folder into n8n
2. Add your OpenRouter API key as a credential
3. Connect your Google Account via OAuth
4. Update Google Sheets nodes with your own spreadsheet URL
5. Activate the workflow

## Testing the Support Bots

Open `frontend/test.html` in your browser to use the chat interface.

Or use curl:
```bash
# Support Bot v1
curl -X POST http://localhost:5678/webhook/support-bot \
  -H "Content-Type: application/json" \
  -d '{"message": "How do I cancel my subscription?"}'

# Support Bot v2
curl -X POST http://localhost:5678/webhook/smart-support \
  -H "Content-Type: application/json" \
  -d '{"question": "How do I reset my password?"}'
```

## Tech Stack
- [n8n](https://n8n.io) - Workflow automation
- [OpenRouter](https://openrouter.ai) - AI model access
- [Google Sheets](https://sheets.google.com) - Data logging
