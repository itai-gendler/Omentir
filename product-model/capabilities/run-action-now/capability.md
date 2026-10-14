---
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#runScheduledActionNowActionImpl
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#executeScheduledActionNow
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#runScheduledActionNowResource
---

# Run action now

The User, or their Connected AI app, sends a lead's next invitation or message right away. It skips the send window and any LinkedIn invitation pause, as the User could in LinkedIn itself, but still keeps the account's five-minute spacing.
