---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#updateAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateAgent
- kind: code
  role: implementation
  target: src/lib/server/data.ts#remapCampaignEnrollments
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#updateAgentResource
---

# Edit agent

The User, or their Connected AI app, changes an agent's targeting, sending account, sequence, send window, tone and what happens when a lead replies. Changes to the sequence apply to every campaign on the agent's lead group, and leads already mid-sequence continue from the matching step. Editing never moves the agent's daily run time.
