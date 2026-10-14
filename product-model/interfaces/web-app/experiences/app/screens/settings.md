---
entities:
- entity: user
  shows:
  - Name
  - Email
  - Profile photo
  - Subscription status
  - Plan
  - Extra LinkedIn accounts
  collects:
  - Extra LinkedIn accounts
- entity: workspace
  shows:
  - Time zone
  - Notification email
  - Daily invite limit
  - Daily message limit
  - First message delay
  - Daily summary
  - Daily summary hour
  - Invite withdrawal
  collects:
  - Time zone
  - Daily invite limit
  - Daily message limit
  - First message delay
  - Daily summary
  - Daily summary hour
  - Invite withdrawal
- entity: linkedin-account
  shows:
  - Display name
  - Photo
  - Connected on
  - Health
entryPoints:
- web-app: /settings
references:
- kind: code
  role: implementation
  target: src/app/(app)/settings/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/settings/settings-view.tsx
- kind: code
  role: implementation
  target: src/app/(app)/settings/linkedin-health-card.tsx
- kind: code
  role: implementation
  target: src/app/(app)/settings/linkedin-seats-card.tsx
---

# Settings

The workspace's settings: time zone, sending limits, notifications and the daily summary, the connected LinkedIn accounts with their health, extra LinkedIn accounts, the subscription, and deleting the workspace.
