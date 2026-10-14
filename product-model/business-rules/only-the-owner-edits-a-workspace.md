---
appliesTo:
- type: entity
  id: workspace
  effect: changes
permits:
- related:
  - {verb: owns, entity: user}
- related:
  - {verb: owns, entity: user}
  - {verb: connects, entity: ai-agent}
references:
- kind: code
  role: implementation
  target: src/lib/server/active-workspace.ts
- kind: code
  role: implementation
  target: src/lib/server/data.ts#findOwnedWorkspace
---

# Only the workspace's owner, or an AI app they connected, changes a workspace

Every page and every agent API call acts on a workspace its User owns.
