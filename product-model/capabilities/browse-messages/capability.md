---
domain: messages
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/(app)/messages/messages-view.tsx
- kind: code
  role: implementation
  target: src/lib/conversation-category.ts#conversationCategory
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#listInboxResource
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#listConversationResources
---

# Browse messages

The User, or their Connected AI app, reads the connected LinkedIn accounts' inbox together with the conversations with leads. Conversations are grouped as Successful (a booked meeting or hot interest), Meetings booked, Interested, Needs a follow up and Denied.
