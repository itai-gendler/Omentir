---
entities:
- entity: agent
  shows:
  - Name
- entity: lead-group
  shows:
  - Name
- entity: lead
  shows:
  - Name
  - Headline
  - Company
  - Location
  - Photo
  - Fit score
- entity: lead-outreach
  shows:
  - Current step
  - Next action at
  - Your messages
  - Prepared message
  - Blocked reason
  collects:
  - Your messages
- entity: conversation
  shows:
  - Messages
references:
- kind: code
  role: implementation
  target: src/app/(app)/agents/[id]/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/actions/activity-dashboard.tsx
- kind: code
  role: implementation
  target: src/app/(app)/actions/action-details.tsx
---

# Agent actions

One agent's upcoming invitations and messages, each with its lead, its time and what will be sent.
