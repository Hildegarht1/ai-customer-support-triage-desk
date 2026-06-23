# Local n8n Setup

This project runs n8n locally with Docker Compose.

## Start n8n

Open PowerShell in this project folder and run:

```powershell
docker compose up -d
```

Open:

```text
http://localhost:5678
```

Create the local owner account when n8n asks.

## Stop n8n

```powershell
docker compose stop
```

## Start It Again

```powershell
docker compose start
```

## View Status

```powershell
docker compose ps
```

## View Logs

```powershell
docker compose logs --tail 100 n8n
```

## Import Workflows

Import these two files from the n8n editor:

```text
workflows/ticket-intake-and-triage.sanitized.json
workflows/admin-approval-commands.sanitized.json
```

The exports intentionally contain placeholders:

```text
YOUR_GOOGLE_SHEET_ID
YOUR_ADMIN_CHAT_ID
```

Replace them in the imported nodes with the real values.

## Reconnect Credentials

Create and select credentials for:

- Telegram Bot API
- Google Sheets OAuth2
- Google Gemini API

Credentials were intentionally removed from the GitHub-safe exports.

## Important Telegram Limitation

Telegram triggers require a public HTTPS webhook. `localhost` alone cannot
receive production Telegram updates.

For initial rebuilding, import and inspect the workflows locally. To test the
Telegram triggers, expose local n8n through a temporary development tunnel and
set n8n's `WEBHOOK_URL` to that public HTTPS address.

Do not treat a temporary tunnel as a production deployment.

## Persistence

The Docker volume `ai-support-n8n-data` stores workflows, credentials, and the
local n8n database. Stopping or replacing the container does not delete this
volume.

Do not run:

```text
docker compose down -v
```

unless you intentionally want to delete the local n8n data.

