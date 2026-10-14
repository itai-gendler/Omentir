---
appliesTo:
- type: entity
  id: agent
  effect: removes
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
  target: src/app/actions.ts#deleteAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteAgent
---

# Only the workspace's owner, or an AI app they connected, deletes an agent

Deleting an agent needs no active subscription, so a User whose subscription lapsed can still remove what they started.
