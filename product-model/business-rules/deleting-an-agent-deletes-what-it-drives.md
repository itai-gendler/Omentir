---
appliesTo:
- type: capability
  id: delete-agent
- type: entity
  id: agent
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteAgent
- kind: code
  role: implementation
  target: src/lib/server/data.ts#persistActivityTotals
---

# Deleting an agent deletes its lead group, campaigns and leads unless another agent fills the same group

Outreach to every lead the agent found ends first. Overview's activity history keeps the counts of what was deleted.
