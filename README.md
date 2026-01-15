# AI Lead Intake & Classification Automation (n8n + LLM)

An end-to-end AI-powered automation built using **n8n** that ingests inbound leads, classifies them using a Large Language Model (LLM), and routes them automatically based on intent, urgency, and lead quality.

This project demonstrates how LLMs can be safely integrated into production-grade automation workflows using deterministic outputs, validation logic, and fallback paths.

---

## Business Use Case

Service-based businesses and agencies often receive leads through multiple channels (forms, landing pages, ads).  
Manual lead review is slow, inconsistent, and leads to delayed responses and missed opportunities.

### Problem
- Leads are manually reviewed and prioritized
- Inconsistent qualification logic
- High response-time latency
- Risk of missing high-intent leads

### Solution
This automation:
- Instantly ingests inbound lead data via webhook
- Uses an LLM to classify lead **intent**, **urgency**, and **quality**
- Assigns a structured lead score
- Automatically routes leads into the appropriate pipeline
- Logs all results for visibility and review

### Impact
- Faster lead response times
- Consistent, repeatable lead qualification
- Reduced manual effort
- Scalable automation-ready architecture

---

## Workflow Architecture

**High-level flow:**

1. Lead data received via webhook
2. Input validation and preprocessing
3. LLM-based lead classification
4. Logic-based routing and scoring
5. CRM-style storage and logging
6. Error handling and fallback paths

---

## AI Classification Logic

The workflow uses an LLM as a **decision engine**, not a free-form generator.

The model is prompted to return a **strict JSON object** containing:
- `intent` (e.g., sales, support, inquiry)
- `urgency` (low / medium / high)
- `lead_score` (numeric)
- `confidence` (0–1)

This ensures downstream automation remains deterministic and safe.

---

## Failure Handling & Reliability

Automation reliability is a core design goal of this project.

Key safeguards include:
- Strict JSON schema enforcement on LLM outputs
- Validation of required fields before routing
- Confidence-based fallback paths for uncertain classifications
- Default routes for unknown or malformed inputs
- Error logging for manual review instead of silent failures

These patterns prevent automation breakage and make the system production-ready.

---

## Tech Stack

- **Automation Platform:** n8n
- **AI / LLM:** OpenAI / OpenRouter
- **API Integration:** Webhooks, REST APIs
- **Data Storage:** Google Sheets (CRM-style logging)
- **Deployment:** Docker
- **Version Control:** Git & GitHub

---

## Sample Input

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "message": "I need pricing details urgently",
  "source": "Website Contact Form"
}


Future Enhancements

GoHighLevel (GHL) CRM integration

Slack / Email alerts for high-priority leads

Human-in-the-loop review for low-confidence cases

Analytics dashboard for lead performance
