---
domain: leads
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/lib/leads-csv.ts#buildLeadsCsv
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#exportLeadsResource
---

# Export leads

The User, or their Connected AI app, exports a lead group as a CSV file: name, title, company, location, LinkedIn profile, fit score, reasons, summary, signal, outreach status and the day each lead was added.
