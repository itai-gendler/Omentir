---
appliesTo:
- type: entity
  id: workspace
  effect: removes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteOwnedWorkspace
- kind: code
  role: implementation
  target: src/lib/server/data.ts#findOwnedWorkspace
---

# Only the workspace's owner deletes it

A User deletes only workspaces they own.
