---
appliesTo:
- type: entity
  id: agent
  effect: changes
  facts:
  - Leads only
permits:
- related:
  - {verb: runs, entity: workspace}
  - {verb: owns, entity: user}
- related:
  - {verb: runs, entity: workspace}
  - {verb: owns, entity: user}
  - {verb: connects, entity: ai-agent}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#setAgentLeadsOnlyActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#allowOutreachOnAgent
---

# Only the workspace's owner, or an AI app they connected, switches an agent between leads only and outreach

Making an agent leads only, or allowing its outreach again, needs no active subscription.
