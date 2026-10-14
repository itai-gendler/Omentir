---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#saveScheduledMessageActionImpl
- kind: code
  role: implementation
  target: src/lib/server/scheduled-actions.ts#saveScheduledMessageEdit
---

# Edit upcoming message

The User rewrites a lead's next sequence message. It is kept for that lead and sent word for word in place of the campaign's message or AI's draft, until the User resets it to the agent's message.
