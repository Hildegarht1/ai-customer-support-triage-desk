# Workflow Architecture

```mermaid
flowchart TD
    A["Customer message"] --> B["n8n trigger"]
    B --> C["Normalize message and create ticket ID"]
    C --> D["Log raw ticket"]
    D --> E["AI classification"]
    E --> F["SLA calculation"]
    F --> G["Knowledge base lookup"]
    G --> H["AI reply draft"]
    H --> I{"Escalation or low confidence?"}
    I -- "Yes" --> J["Escalate to human"]
    I -- "No" --> K["Send approval request"]
    K --> L{"Admin decision"}
    L -- "Approve" --> M["Send customer reply"]
    L -- "Reject" --> N["Hold draft"]
    L -- "Escalate" --> J
    J --> O["Update ticket and audit log"]
    M --> O
    N --> O
```

## System Boundaries

The AI does not issue refunds, change account settings, make legal promises, or guarantee timelines. It drafts replies and routing recommendations only.

## Reliability Features

- Raw ticket logged before AI processing
- Structured classification output
- Confidence thresholds
- Escalation rules
- Human approval before external replies
- SLA monitoring
- Audit log for major events

## What To Show In A Portfolio

- Screenshot of the n8n workflow canvas
- Screenshot of the support ticket database
- Screenshot of the knowledge base
- Screenshot of the admin approval message
- Screenshot of the AI-generated draft reply
- Short demo video showing a customer message being triaged

