---
appliesTo:
- type: capability
  id: create-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#createAgentResource
- kind: code
  role: implementation
  target: src/app/actions.ts#createAgentAndDiscoverLeadsActionImpl
---

# A Steal Customers agent always runs AI-written outreach

Its campaign is created with the agent and its messages are written by AI from each lead's post and comment; it has no leads-only form and takes no messages written in advance.
