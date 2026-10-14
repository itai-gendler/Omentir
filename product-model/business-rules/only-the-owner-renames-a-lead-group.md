---
appliesTo:
- type: entity
  id: lead-group
  effect: changes
  facts:
  - Name
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
  target: src/lib/server/data.ts#renameGroup
---

# Only the workspace's owner, or an AI app they connected, renames a lead group

A lead group is renamed by renaming it on its agent.
