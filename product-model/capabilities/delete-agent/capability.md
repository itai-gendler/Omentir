---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#deleteAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteAgent
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
---

# Delete agent

The User, or their Connected AI app, deletes an agent. Outreach to every lead it found stops, and unless another agent fills the same lead group, the group, its campaigns and its leads are deleted too. Deleting works with or without an active subscription.
