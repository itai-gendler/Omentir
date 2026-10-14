---
entities:
- entity: conversation
  shows:
  - Messages
  - Reply intent
  - Intent reason
  - Meeting booked at
  - Category
- entity: linkedin-chat
  shows:
  - Participant
  - Messages
  - Unread
- entity: lead
  shows:
  - Name
  - Headline
  - Company
  - Photo
  - Fit score
- entity: linkedin-account
  shows:
  - Display name
entryPoints:
- web-app: /messages
references:
- kind: code
  role: implementation
  target: src/app/(app)/messages/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/messages/messages-view.tsx
---

# Messages

The connected LinkedIn accounts' inbox together with the conversations with leads, grouped as Successful, Meetings booked, Interested, Needs a follow up and Denied.
