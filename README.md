# AI Customer Support Triage Desk

An AI-assisted support automation that receives customer messages, classifies urgency and intent, searches a knowledge base, drafts replies, escalates risky cases, and logs every ticket for tracking.

## Recruiter-Friendly Project Page

This repository includes a static project page:

```text
index.html
```

Host it with GitHub Pages so recruiters can click one link and understand the project without accessing the private n8n editor.

See:

```text
github-pages-guide.md
```

## What This Project Demonstrates

- Low-code customer support automation with n8n
- AI classification for intent, sentiment, priority, and routing
- Retrieval-style knowledge base answering
- Human-in-the-loop approval before customer-facing replies
- SLA and escalation logic
- Ticket logging, audit trails, and support reporting

## Recommended Free/Low-Cost Stack

- n8n self-hosted community edition
- Telegram bot or Gmail as the customer message channel
- Google Sheets or Airtable as the ticket database
- Google Docs, Notion, or a Google Sheet tab as the knowledge base
- Gmail or Telegram for responses
- OpenAI, Gemini, Groq, or another LLM provider for classification and drafting

## Workflow Summary

1. A customer sends a message through Telegram, email, or a website form.
2. n8n receives the message.
3. The workflow creates a ticket ID and logs the raw message.
4. AI classifies:
   - intent
   - sentiment
   - urgency
   - department
   - reply confidence
5. The workflow searches the knowledge base for relevant answers.
6. AI drafts a reply using only approved knowledge base content.
7. If confidence is high and risk is low, the reply is sent for human approval.
8. If confidence is low, sentiment is negative, or urgency is high, the ticket is escalated.
9. The ticket status and audit log are updated.

## Workflow Exports

Sanitized n8n workflow exports are in:

```text
workflows/
```

Before committing any new export:

- Remove credentials.
- Remove API keys, tokens, and private URLs.
- Remove real customer data.
- Keep sample ticket data only.

Current sanitized exports:

```text
workflows/ticket-intake-and-triage.sanitized.json
workflows/admin-approval-commands.sanitized.json
```

## Minimum Viable Version

Build this first:

- Telegram or Gmail trigger
- AI classification
- Google Sheets ticket log
- AI draft reply
- Telegram admin approval message

That version can be completed in 1-2 focused days.

## Portfolio Version

Add these to make it CV-worthy:

- Knowledge base lookup
- Confidence scoring
- Escalation rules
- SLA timer
- Human approval before sending replies
- Support dashboard
- Audit log
- Demo video

That version usually takes 4-7 days if you are learning as you build.

## Demo Scenario

Use a fictional SaaS company called FlowDesk.

Example customer message:

```text
I upgraded my plan yesterday but my account still says Free. I need this fixed today because my team cannot access the automation dashboard.
```

The system should classify this as:

- Intent: billing/account access
- Sentiment: frustrated
- Urgency: high
- Department: billing/support
- Escalation: yes

## Suggested Build Order

1. Create the Google Sheet using `data-schema.md`.
2. Create a small FAQ knowledge base using `knowledge-base-sample.md`.
3. Connect Telegram or Gmail to n8n.
4. Create the ticket logging workflow.
5. Add the AI classification prompt from `prompts.md`.
6. Add knowledge base lookup.
7. Add AI reply drafting.
8. Add human approval or escalation logic.
9. Add status updates and audit logs.
10. Record a 2-3 minute demo using `demo-script.md`.
