# Setup Checklist

## Accounts Needed

- n8n self-hosted or n8n trial
- Google account
- Telegram account
- LLM API account

## Before Building In n8n

- Create a Telegram bot using BotFather.
- Get your Telegram chat ID.
- Create a Google Sheet with these tabs: Tickets, Knowledge Base, Audit Log, SLA Rules.
- Add the sample knowledge base rows from `knowledge-base-sample.md`.
- Choose your LLM provider.

## Build Milestone 1

- Telegram trigger receives a message.
- Message is normalized.
- Ticket ID is generated.
- Raw ticket is logged in Google Sheets.

## Build Milestone 2

- AI classifies the ticket.
- Classification JSON is parsed.
- Ticket row is updated with intent, urgency, sentiment, department, and confidence.

## Build Milestone 3

- Knowledge base lookup returns relevant rows.
- AI drafts a safe reply using only the knowledge base.
- Reply draft is stored in the ticket row.

## Build Milestone 4

- High-risk tickets are escalated.
- Low-risk tickets are sent to admin approval.
- Admin can approve, reject, or escalate.

## Build Milestone 5

- SLA monitor checks open tickets.
- Overdue tickets trigger an admin alert.
- Audit log records all major events.

## Final Portfolio Polish

- Add screenshots.
- Record a 2-3 minute demo.
- Add architecture diagram.
- Add CV bullet.
- Write a short case study.

