AI Customer Support Triage Desk
An AI-assisted support automation that receives customer messages, classifies urgency and intent, searches a knowledge base, drafts replies, escalates risky cases, and logs every ticket for tracking.

What This Project Demonstrates
Low-code customer support automation with n8n
AI classification for intent, sentiment, priority, and routing
Retrieval-style knowledge base answering
Human-in-the-loop approval before customer-facing replies
SLA and escalation logic
Ticket logging, audit trails, and support reporting
Recommended Free/Low-Cost Stack
n8n self-hosted community edition
Telegram bot or Gmail as the customer message channel
Google Sheets or Airtable as the ticket database
Google Docs, Notion, or a Google Sheet tab as the knowledge base
Gmail or Telegram for responses
OpenAI, Gemini, Groq, or another LLM provider for classification and drafting
Workflow Summary
A customer sends a message through Telegram, email, or a website form.
n8n receives the message.
The workflow creates a ticket ID and logs the raw message.
AI classifies:
intent
sentiment
urgency
department
reply confidence
The workflow searches the knowledge base for relevant answers.
AI drafts a reply using only approved knowledge base content.
If confidence is high and risk is low, the reply is sent for human approval.
If confidence is low, sentiment is negative, or urgency is high, the ticket is escalated.
The ticket status and audit log are updated.
Minimum Viable Version
Build this first:

Telegram or Gmail trigger
AI classification
Google Sheets ticket log
AI draft reply
Telegram admin approval message
That version can be completed in 1-2 focused days.

Portfolio Version
Add these to make it CV-worthy:

Knowledge base lookup
Confidence scoring
Escalation rules
SLA timer
Human approval before sending replies
Support dashboard
Audit log
Demo video
That version usually takes 4-7 days if you are learning as you build.

Demo Scenario
Use a fictional SaaS company called FlowDesk.

Example customer message:

I upgraded my plan yesterday but my account still says Free. I need this fixed today because my team cannot access the automation dashboard.
The system should classify this as:

Intent: billing/account access
Sentiment: frustrated
Urgency: high
Department: billing/support
Escalation: yes
Suggested Build Order
Create the Google Sheet using data-schema.md.
Create a small FAQ knowledge base using knowledge-base-sample.md.
Connect Telegram or Gmail to n8n.
Create the ticket logging workflow.
Add the AI classification prompt from prompts.md.
Add knowledge base lookup.
Add AI reply drafting.
Add human approval or escalation logic.
Add status updates and audit logs.
Record a 2-3 minute demo using demo-script.md.
