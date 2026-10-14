---
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/lib/server/scheduled-actions.ts#listScheduledActions
- kind: code
  role: implementation
  target: src/app/(app)/actions/activity-dashboard.tsx
- kind: code
  role: implementation
  target: src/app/(app)/actions/action-details.tsx
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#listScheduledActionResources
---

# Browse upcoming actions

The User, or their Connected AI app, reads what outreach will do next: each upcoming invitation and message with its lead, its time and the exact message that will be sent, or why it is blocked. The User sees them per agent and per lead.
