---
entities:
- entity: user
  shows:
  - Subscription status
- entity: workspace
  shows:
  - Demo booking link
  - Deal size
  collects:
  - Demo booking link
  - Deal size
- entity: linkedin-account
  shows:
  - Display name
- entity: lead
  shows:
  - Name
  - Headline
  - Company
  - Fit score
- entity: conversation
  shows:
  - Reply intent
  - Meeting booked at
entryPoints:
- web-app: /overview
references:
- kind: code
  role: implementation
  target: src/app/(app)/overview/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/overview/overview-view.tsx
- kind: code
  role: implementation
  target: src/app/(app)/overview/overview-setup.tsx
---

# Overview

The workspace's home. Until the workspace is set up it is the setup checklist: an active subscription, a connected LinkedIn account, a demo booking link and a first agent. Afterwards it shows outreach results for a chosen period.
