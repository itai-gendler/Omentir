---
appliesTo:
- type: capability
  id: send-linkedin-message
- type: capability
  id: send-sequence-message
- type: capability
  id: record-lead-reply
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createConversationMessage
- kind: code
  role: implementation
  target: src/lib/server/owner-message-guard.ts#stopForOwnerMessage
---

# Once the User writes to a lead themselves, Omentir sends that lead nothing more automatically

A message the User sends from Omentir or from LinkedIn itself stops every running outreach and AI answer for that lead.
