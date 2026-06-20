# AI Agency Voice Automation System (n8n)

This repository contains a comprehensive suite of automation workflows built in [n8n](https://n8n.io/) to manage inbound and outbound AI voice call routing, transcript distribution, and lead follow-up.

## Features

* **Outbound Call Trigger:** Monitors HubSpot for specific lead form submissions or CRM property changes (`ai_call_trigger`) and dispatches a call via Retell AI. It verifies timezone and ensures duplicates are not executed.
* **Inbound Call Master Workflow:** Processes incoming webhook payloads from your AI voice agent when calls complete. It automatically routes summaries, tracks metrics, and sends Slack alerts.
* **Outbound Master Workflow:** Follow-up triggers that automatically send booking links (via SMS/Email) if requested by the lead during the call, alongside routing transcripts and call recordings to team members.
* **Accounting/Voicemail Alerts:** Automatically routes specific user requests (e.g., "I have a question about an invoice" or "I want to leave a message") to designated team members' email inboxes.

## Workflows Included

1. `Outbound Call Trigger.json`
2. `Master Workflow (Inbound+ Tools).json`
3. `Master Workflow (Outbound Tools).json`

## Setup & Installation

1. **Import Workflows:** Open your n8n instance. Go to **Workflows > Import from File** and upload the JSON files from this repository.
2. **Configure Credentials:**
   You will need to re-authenticate or set up the following credentials in your n8n instance:
   * HubSpot OAuth2 API
   * Gmail OAuth2 (for routing emails)
   * Twilio API (for SMS triggers)
   * Slack API (for internal alerts)
3. **Update Placeholders:**
   Before activating, open the workflow nodes and replace placeholder text:
   * Retell AI Authorization Bearer Token (`YOUR_RETELL_API_KEY_HERE`)
   * Retell `agent_id`
   * Your Company/Team Emails (`team1@example.com`)
   * Internal Slack Channel IDs (`YOUR_SLACK_CHANNEL_ID`)
   * Twilio Sender Numbers (`+12345678900`)
   * Calendar links (`meetings.hubspot.com/YOUR_CALENDAR_LINK`)

## Security Note
Make sure you **never commit active API keys, internal IDs, or personal email addresses** to this repository. All provided templates are fully sanitized for public sharing.
