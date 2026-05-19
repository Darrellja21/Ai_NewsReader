## AI News Daily Digest — n8n Automation Workflow

Automated daily delivery of curated AI news to Discord, powered by n8n, Docker, and ngrok.

## What It Does

Every morning at **10:00 AM**, this workflow automatically:

- Fetches the latest AI industry news
- Passes headlines through an AI summarisation step
- Formats and posts a clean digest to a Discord channel via webhook

No manual intervention. No missed updates.

## Architecture
Cron Trigger (10AM daily)
↓
Fetch AI News
↓
AI Summarise
↓
Discord Webhook → #ai-news channel

## How It's Deployed

- **n8n** runs inside a Docker container for isolated, reproducible execution
- **ngrok** provides a persistent static domain (free tier static domain feature), meaning the public URL remains consistent across restarts — no paid hosting required
- This replicates a production-like deployment environment at zero infrastructure cost

## Tech Stack

| Tool | Role |
|------|------|
| n8n | Workflow automation engine |
| Docker Desktop | Container runtime |
| ngrok | Persistent public tunnel to local container |
| Discord Webhook | Notification delivery |

## Setup

### Prerequisites

- Docker Desktop installed
- ngrok account (free tier with static domain)
- Discord server with webhook enabled

### Run It

Start the n8n Docker container:

```bash
docker run -it --rm -p 5678:5678 n8nio/n8n
```

In a separate terminal, expose it via your ngrok static domain:

```bash
ngrok http --domain=https://football-dawdler-cricket.ngrok-free.dev
```

Then import `workflow.json` into your n8n instance and update the Discord webhook URL in the workflow settings.

## Workflow File

`workflow.json` — exported directly from n8n. Import via **n8n → Settings → Import Workflow**.

After importing, update the Discord Webhook URL node with your own server's webhook before activating.

## Why I Built This

Keeping up with AI developments manually is slow and inconsistent. This workflow removes that friction entirely — a structured digest arrives in Discord every morning without any input from me. It also served as a practical exercise in container deployment, public tunnelling, and event-driven workflow design using n8n.

## Author

**Darrell John Abrahams**
Diploma in Information Technology — Multimedia University, Cyberjaya
