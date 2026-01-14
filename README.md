🚀 AI Lead Intake & Classification Automation (n8n + LLM)

End-to-end AI-powered lead intake system that classifies incoming leads by intent, urgency, and category, routes them automatically, and stores structured data for CRM-style tracking.

🔹 Features

Webhook API for real-time lead ingestion

LLM-based intent detection, urgency classification & lead scoring

Deterministic JSON outputs for production safety

Automated routing into Sales / Support pipelines

Google Sheets persistence for CRM-style visibility

Clean API response for frontend or system integration

🔹 Tech Stack

n8n (Workflow automation)

OpenAI Chat Model

JavaScript Code Nodes

Google Sheets API

REST Webhooks

🔹 Workflow Overview

Incoming lead via webhook

Input validation

LLM-based classification & scoring

Business-rule routing

Persistent storage in Google Sheets

JSON response returned to client


Sample API Request

{
  "name": "John Doe",
  "email": "john@company.com",
  "message": "We want AI automation for invoice processing",
  "source": "website"
}



Sample API Response

{
  "status": "success",
  "lead": {
    "name": "John Doe",
    "email": "john@company.com",
    "category": "sales",
    "intent": "high",
    "urgency": "immediate",
    "lead_score": 90
  }
}


🔧 Future upgrades: CRM integrations, Slack alerts, human-in-the-loop review, vector memory.

## Security Notes
- Secrets managed via environment variables
- `.env` excluded from version control
- Deterministic LLM outputs to avoid prompt injection risks
