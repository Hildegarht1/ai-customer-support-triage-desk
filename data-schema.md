# Data Schema

Use this as the Google Sheets or Airtable structure.

## Sheet: Tickets

| Column | Example | Notes |
|---|---|---|
| ticket_id | TCK-20260525-143000 | Unique ID generated in n8n |
| created_at | 2026-05-25 14:30 | Timestamp |
| channel | Telegram | Telegram, Gmail, Web Form |
| customer_name | Daniel Reed | From message metadata or form |
| customer_contact | @danielreed | Email, Telegram ID, or phone |
| raw_message | I upgraded my plan yesterday... | Original message |
| intent | billing_account_access | AI classification |
| department | Billing | AI classification |
| sentiment | Frustrated | AI classification |
| urgency | High | Low, Medium, High, Critical |
| confidence | 0.82 | AI confidence score |
| escalation_required | Yes | Yes or No |
| status | Pending approval | New, Pending approval, Escalated, Replied, Closed |
| draft_reply | Thanks for reaching out... | AI-generated draft |
| approved_reply | Thanks for reaching out... | Final response after approval |
| assigned_to | Support Lead | Optional |
| sla_due_at | 2026-05-25 16:30 | Calculated due time |
| last_updated | 2026-05-25 14:35 | Timestamp |

## Sheet: Knowledge Base

| Column | Example | Notes |
|---|---|---|
| article_id | KB-001 | Unique ID |
| topic | Billing plan upgrade delay | Searchable topic |
| keywords | billing, upgrade, plan, account | Used for simple lookup |
| answer | Plan upgrades can take up to... | Approved support answer |
| escalation_rule | Escalate if access is blocked | Optional |
| owner | Billing | Responsible team |
| last_reviewed | 2026-05-01 | Freshness check |

## Sheet: Audit Log

| Column | Example | Notes |
|---|---|---|
| event_id | EVT-0001 | Unique ID |
| timestamp | 2026-05-25 14:35 | Timestamp |
| ticket_id | TCK-20260525-143000 | Link to Tickets sheet |
| event_type | TICKET_CLASSIFIED | Event label |
| details | Intent billing_account_access, urgency High | Human-readable log |
| actor | n8n | n8n, AI, Admin |

## Sheet: SLA Rules

| Urgency | Response Target | Escalation |
|---|---|---|
| Low | 24 hours | No |
| Medium | 8 hours | No |
| High | 2 hours | Yes |
| Critical | 30 minutes | Yes |

