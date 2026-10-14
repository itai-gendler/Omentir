---
domain: messages
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#completeConversationManualFollowUpActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#completeConversationManualFollowUp
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#completeFollowUpResource
---

# Mark follow-up done

The User, or their Connected AI app, marks a conversation's follow-up done. It leaves Needs a follow up until the lead replies again.
