---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#launchAgentFromSetupActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#launchOutreachAgentFromSetupActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#createAgentAndDiscoverLeadsActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#createCampaignActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgent
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createCampaign
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#createAgentResource
- kind: code
  role: implementation
  target: src/app/(app)/agents/new-agent-button.tsx
---

# Create agent

The User, or their Connected AI app, starts an agent. Only Lead finds and scores people into a lead group; Leads + outreach also runs a campaign on them; Outreach only imports LinkedIn profiles from a CSV and runs a campaign without discovery; Steal Customers finds people commenting on competitors' LinkedIn posts and reaches out with AI. A new agent looks for leads right away and then daily at the time it was created.
