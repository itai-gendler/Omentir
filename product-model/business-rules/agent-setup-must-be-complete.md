---
appliesTo:
- type: capability
  id: create-agent
- type: capability
  id: edit-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgent
- kind: code
  role: implementation
  target: src/lib/steal-customers-targeting.ts#targetingFromProductProfile
---

# An agent starts only with its targeting complete

A classic agent needs a prospect description, job titles, industries, locations and keywords; a Steal Customers agent needs at least one competitor page or founder or employee profile, and a company profile with a company name, description or pain points. Outreach only agents need none.

## Rationale

Partial targeting finds people outside the ideal customer profile, who would then be contacted.
