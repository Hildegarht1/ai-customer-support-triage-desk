# Demo Script

## Demo Goal

Show that the automation can receive a customer issue, classify it, draft a safe reply, and escalate it when the risk is high.

## Demo Steps

1. Show the support knowledge base.
2. Show the Google Sheet ticket database.
3. Send the sample customer message through Telegram.
4. Open n8n and show the workflow execution.
5. Show the ticket row created in Google Sheets.
6. Show the AI classification:
   - Intent: billing/account access
   - Urgency: High
   - Sentiment: Frustrated
   - Department: Billing
   - Escalation required: Yes
7. Show the drafted reply.
8. Show the admin escalation message in Telegram.
9. Show the audit log entry.
10. Explain that the AI did not send a risky customer-facing message without human review.

## Suggested Talk Track

```text
This project is an AI customer support triage desk built with low-code automation. A customer message comes in through Telegram, then n8n creates a ticket, classifies the issue with AI, checks the knowledge base, drafts a response, and decides whether it can go to approval or must be escalated.

In this example, the customer has a billing and account access problem. Because the message is urgent and affects paid access, the system routes it to a human instead of automatically replying. This keeps the workflow useful while avoiding risky AI decisions.
```

## Time Saved Claim

Use careful language:

```text
In a simulated support workflow, this reduced first-pass triage from several minutes of manual reading and routing to an automated classification and escalation step completed in under one minute.
```

