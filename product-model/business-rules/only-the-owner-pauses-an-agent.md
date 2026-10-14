---
appliesTo:
- type: entity
  id: agent
  effect: changes
  to: Paused
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
  target: src/app/actions.ts#pauseAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#pauseAgent
---

# Only the workspace's owner, or an AI app they connected, pauses an agent

Pausing needs no active subscription, so a User can always stop outreach.
