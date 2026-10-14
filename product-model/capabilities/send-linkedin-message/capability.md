---
domain: messages
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#sendLinkedInChatMessageActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#sendLeadReplyActionImpl
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#sendReplyToLead
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#replyToChatResource
- kind: code
  role: implementation
  target: src/lib/server/data.ts#recordManualActionSlot
---

# Send LinkedIn message

The User, or their Connected AI app, writes to a lead or replies in a LinkedIn chat from the account that owns it, with attachments if wanted. A person writing is not automation: no send window or daily cap blocks it, though it counts toward the day's messages and pushes the account's next automated action back. Writing to a lead yourself ends that lead's automated outreach.
