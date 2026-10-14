---
domain: leads
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#deleteGroupActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteGroup
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#deleteGroupResource
---

# Delete lead group

The User, or their Connected AI app, deletes a lead group that no agent or campaign uses, with its leads, their outreach and conversations. The activity totals on Overview keep their history.
