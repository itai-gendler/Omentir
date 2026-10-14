---
availability:
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#importCsvLeadsResource
- kind: code
  role: implementation
  target: src/lib/linkedin-csv.ts#parseLinkedInLeadCsv
- kind: code
  role: implementation
  target: src/app/actions.ts#importLinkedInCsvLeadsActionImpl
---

# Import leads

A Connected AI app imports LinkedIn profiles from a CSV into an Outreach only agent's lead group, so its campaign contacts them. In the app, importing is part of creating an Outreach only agent.
