---
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#stopLeadOutreachActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#stopLeadOutreach
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#stopLeadOutreachResource
---

# Stop lead outreach

The User, or their Connected AI app, stops outreach to a lead: every running sequence and AI reply for that lead ends. A lead not contacted yet is marked stopped; one already contacted keeps the stage reached.
