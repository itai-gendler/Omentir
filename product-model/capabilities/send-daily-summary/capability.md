---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#sendDailyDigests
- kind: code
  role: implementation
  target: src/lib/daily-digest.ts#shouldSendDailyDigest
---

# Send daily summary

When a subscribed workspace has the daily summary on, Omentir emails the last 24 hours of new leads, invitations, accepted connections, messages and replies at the chosen local hour, once a day.
