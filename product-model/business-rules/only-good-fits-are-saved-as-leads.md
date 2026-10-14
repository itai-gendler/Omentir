---
appliesTo:
- type: capability
  id: discover-leads
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runAgents
---

# A searched person is saved as a lead only with a fit score of 65 or more and inside the agent's locations

Broad search matches are scored by AI against the company profile before anyone is saved, so people who would be a poor fit never enter a campaign.
