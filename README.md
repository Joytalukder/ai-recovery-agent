# AI Business Recovery Agent

An AI-powered customer support and business recovery automation system built with **n8n, AI Agents, Google Sheets, and Telegram**.

## Overview

The AI Business Recovery Agent helps businesses manage customer complaints, analyze customer messages, prioritize issues, and notify business owners when human intervention may be required.

The workflow receives customer information through a webhook, processes it using an AI Agent, stores customer records in Google Sheets, and routes urgent cases to Telegram notifications.

## Key Features

- **Automated Customer Intake:** Receives customer messages through an HTTP webhook.
- **AI-Powered Complaint Analysis:** Identifies customer intent and summarizes issues.
- **Lead Classification:** Classifies leads as Hot, Warm, or Cold.
- **Priority Assessment:** Assigns a priority level to customer issues.
- **Automated Response Generation:** Creates professional customer reply suggestions.
- **Customer Data Management:** Stores customer information and AI analysis in Google Sheets.
- **Urgent Case Detection:** Uses conditional logic to identify cases requiring human review.
- **Telegram Notifications:** Sends alerts for cases routed through the urgent branch.

## Tech Stack

- n8n — Workflow automation
- AI Agent — Customer message analysis and response generation
- Google Sheets — Customer records and lead tracking
- Telegram Bot API — Notifications
- Webhooks and JSON — Data exchange
- JavaScript — Data transformation in n8n Code nodes

## Workflow Architecture

```text
Customer Request
      |
      v
Webhook (POST)
      |
      v
Edit Fields
      |
      v
AI Agent
      |
      v
Code / JSON Parsing
      |
      v
Google Sheets
      |
      v
IF: Human Review Required?
      |
      +---- True ----> Telegram Alert
      |
      +---- False ---> Continue Workflow
```

*The diagram represents the intended workflow architecture. Confirm that each connection and branch is working in your n8n instance before claiming end-to-end completion.*

## Example Input

```json
{
  "customer_name": "Rahim",
  "phone": "+8801712345678",
  "message": "I ordered a table, but it has not arrived yet.",
  "business_name": "Joy's Furniture"
}
```

## Example AI Output

```json
{
  "customer_name": "Rahim",
  "intent": "Delayed delivery complaint",
  "lead_status": "Warm",
  "priority": "High",
  "reply": "We apologize for the delay. Our team will review your order and follow up with you.",
  "needs_human": true
}
```

*Example output only. Actual AI results may vary depending on the model and prompt.*

## Setup Instructions

### 1. Import or Build the Workflow

Open your n8n instance and create a new workflow. Add the required Webhook, Edit Fields, AI Agent, Code, Google Sheets, IF, and Telegram nodes as needed.

### 2. Configure the Webhook

- HTTP Method: `POST`
- Path: `Business-recovery`
- Test the workflow using the Webhook Test URL.

### 3. Configure the AI Agent

Connect a supported chat model and configure the agent to analyze customer intent, assign priority, classify leads, generate reply suggestions, and determine whether human review is needed.

### 4. Connect Google Sheets

Create a spreadsheet with these columns:

- customer_name
- phone
- message
- intent
- lead_status
- priority
- reply
- needs_human

Configure the Google Sheets node to append a row.

### 5. Configure Telegram Notifications

Create a Telegram bot using [@BotFather](https://t.me/BotFather). Add the bot credentials to n8n and configure the Telegram node with your Chat ID.

Keep bot tokens and other credentials private.

### 6. Test the Workflow

Send a POST request with customer JSON data. Verify that the AI output is correct, the Google Sheets row is saved, and the IF node routes urgent cases to Telegram.

### 7. Activate the Workflow

After testing, activate the workflow and configure the production webhook URL if you want to receive live requests.

## Use Cases

- E-commerce delivery complaints
- Furniture store customer support
- Lead qualification and follow-up
- Customer service escalation
- Small business support automation
- Customer relationship management (CRM)

## Security Considerations

- Never commit API keys, bot tokens, passwords, or private customer information.
- Use n8n credentials for external service authentication.
- Validate incoming webhook data.
- Restrict access to customer records.
- Review AI-generated responses before taking sensitive business actions.

## Future Improvements

- WhatsApp Business integration
- Automatic customer follow-up reminders
- CRM integrations
- Customer sentiment analysis
- Business performance dashboards
- Human approval before sending customer replies

## Project Status

**Development and testing:** In progress until all workflow branches have been verified end to end.

## Author

**Joy Talukder**

AI Automation Developer | n8n | AI Agents | Workflow Automation

- GitHub: [Joytalukder](https://github.com/Joytalukder)
- LinkedIn: [Joy Talukder](https://www.linkedin.com/in/joy-talukder-3b08b036a/)

---

*Built to demonstrate practical AI-powered business workflow automation.*
