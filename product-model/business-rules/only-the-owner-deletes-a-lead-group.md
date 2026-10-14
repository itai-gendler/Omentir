---
appliesTo:
- type: entity
  id: lead-group
  effect: removes
permits:
- related:
  - {verb: contains, entity: workspace}
  - {verb: owns, entity: user}
- related:
  - {verb: contains, entity: workspace}
  - {verb: owns, entity: user}
  - {verb: connects, entity: ai-agent}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#deleteGroupActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteGroup
---

# Only the workspace's owner, or an AI app they connected, deletes a lead group

Deleting a lead group needs no active subscription.
