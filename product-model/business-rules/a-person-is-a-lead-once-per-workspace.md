---
appliesTo:
- type: capability
  id: discover-leads
- type: capability
  id: import-leads
- type: capability
  id: create-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#upsertLead
---

# Each person is one lead per workspace, kept by the agent that found them first

A person found again, by the same or another agent or by an import, is not added twice; the first agent stays their source and their outreach stage is never reset by finding them again.
