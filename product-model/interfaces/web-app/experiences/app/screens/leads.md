---
entities:
- entity: lead-group
  shows:
  - Name
  - Lead count
- entity: lead
  shows:
  - Name
  - Headline
  - Company
  - Location
  - LinkedIn profile
  - Photo
  - Summary
  - Fit score
  - Score reasons
  - Lead reason
  - Engagement
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
entryPoints:
- web-app: /leads
references:
- kind: code
  role: implementation
  target: src/app/(app)/leads/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/leads/leads-view.tsx
---

# Leads

Every lead by lead group, searchable, with a lead's outreach: the steps done and to come, the next action and the conversation so far.
