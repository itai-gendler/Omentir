---
entities:
- entity: workspace
  shows:
  - Company name
  - Description
  - Pain points
  - Demo booking link
  collects:
  - Company name
  - Description
  - Pain points
- entity: linkedin-account
  shows:
  - Display name
- entity: agent
  shows:
  - Name
  - Type
  - Prospect description
  - Job titles
  - Industries
  - Locations
  - Keywords
  - Competitor pages
  - Sending account
  collects:
  - Name
  - Type
  - Prospect description
  - Job titles
  - Industries
  - Locations
  - Keywords
  - Competitor pages
  - Sending account
- entity: lead-group
  shows:
  - Name
  collects:
  - Name
- entity: campaign
  shows:
  - Steps
  - Send window
  - When a lead replies
  - Booking link
  - Email me when a lead replies
  - Goal
  - Message tone
  collects:
  - Steps
  - Send window
  - When a lead replies
  - Booking link
  - Email me when a lead replies
  - Goal
  - Message tone
- entity: lead
  collects:
  - Name
  - LinkedIn profile
  - Headline
  - Company
entryPoints:
- web-app: /agents/new
references:
- kind: code
  role: implementation
  target: src/app/(app)/agents/new/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/agents/new/agent-setup.tsx
- kind: code
  role: implementation
  target: src/app/(app)/agents/new-agent-button.tsx
---

# Agent setup

Where the User creates or edits an agent: what kind of agent it is, who it looks for, the competitor pages or CSV list it starts from, the outreach sequence, when it may send and who owns the conversation once a lead replies, then a review before launch.
