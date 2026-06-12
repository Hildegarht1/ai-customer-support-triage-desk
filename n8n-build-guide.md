# n8n Build Guide

This guide describes the workflow to build manually in n8n.

## Workflow 1: New Message To Support Ticket

### Node 1: Trigger

Choose one:

- Telegram Trigger for a chat-based demo
- Gmail Trigger for an email support demo
- Webhook Trigger for a website form demo

For a beginner-friendly version, use Telegram.

### Node 2: Set / Edit Fields

Purpose: normalize the incoming message.

Create these fields:

- ticket_id
- created_at
- channel
- customer_name
- customer_contact
- raw_message
- status

Suggested ticket ID:

```text
TCK-{{$now.format('yyyyMMdd-HHmmss')}}
```

Set initial status:

```text
New
```

### Node 3: Add Ticket Row

Purpose: log the raw customer message before AI processing.

Add a row to the `Tickets` sheet.

### Node 4: AI Classification

Purpose: classify the ticket.

Use the classification prompts from `prompts.md`.

Expected output:

- intent
- department
- sentiment
- urgency
- confidence
- escalation_required
- reasoning_summary
- missing_information

### Node 5: Parse Classification JSON

Purpose: convert the AI classification into usable workflow fields.

If parsing fails, route the ticket to manual review.

### Node 6: Calculate SLA

Purpose: assign a response target based on urgency.

Suggested rules:

- Low: 24 hours
- Medium: 8 hours
- High: 2 hours
- Critical: 30 minutes

### Node 7: Knowledge Base Lookup

Purpose: find relevant approved answers.

Simple free-plan approach:

- Store FAQs in a Google Sheet tab called `Knowledge Base`.
- Search by keywords or topic.
- Pass the top matches into the reply drafting prompt.

More advanced version:

- Use Supabase free tier with embeddings.
- Use a vector search step.

### Node 8: AI Reply Draft

Purpose: create a draft reply using only knowledge base content.

Use the reply drafting prompts from `prompts.md`.

### Node 9: IF Escalation Or Low Confidence

Escalate if any of these are true:

- urgency is High or Critical
- escalation_required is true
- classification confidence is below 0.7
- reply confidence is below 0.75
- missing_information is not empty

### Node 10A: Escalation Path

Actions:

- Update ticket status to `Escalated`
- Send Telegram message to admin
- Add audit log event `TICKET_ESCALATED`

### Node 10B: Approval Path

Actions:

- Update ticket status to `Pending approval`
- Send Telegram approval message to admin
- Add audit log event `DRAFT_READY_FOR_APPROVAL`

## Workflow 2: Admin Approval To Customer Reply

### Node 1: Telegram Trigger

Listen for admin commands:

```text
APPROVE TCK-20260525-143000
ESCALATE TCK-20260525-143000
REJECT TCK-20260525-143000
```

### Node 2: Parse Command

Extract:

- action
- ticket_id

### Node 3: Lookup Ticket

Find the ticket row by `ticket_id`.

### Node 4: IF Action

If APPROVE:

- send reply to customer through the original channel if possible
- update status to `Replied`
- add audit event `CUSTOMER_REPLY_SENT`

If ESCALATE:

- update status to `Escalated`
- send escalation message to the right department
- add audit event `MANUAL_ESCALATION_REQUESTED`

If REJECT:

- update status to `Draft rejected`
- add audit event `DRAFT_REJECTED`

## Workflow 3: SLA Monitor

Run every 15-30 minutes.

Steps:

1. Read open tickets from the Tickets sheet.
2. Check if `sla_due_at` is near or overdue.
3. Send admin alert for overdue tickets.
4. Update audit log.

This workflow makes the project feel much more like a real support operations system.

## Error Handling

Create an error workflow later that notifies you when:

- AI output cannot be parsed
- Google Sheets update fails
- Telegram send fails
- Gmail send fails

Log errors to the Audit Log sheet.

