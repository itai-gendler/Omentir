---
appliesTo:
- type: capability
  id: delete-lead-group
- type: entity
  id: lead-group
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteGroup
---

# A lead group that an agent fills or a campaign contacts cannot be deleted

The agent or campaign must be deleted first; deleting the agent removes its group as well.
