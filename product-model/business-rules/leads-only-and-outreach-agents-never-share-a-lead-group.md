---
appliesTo:
- type: capability
  id: create-agent
- type: capability
  id: edit-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createCampaign
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgent
---

# A lead group filled by a leads-only agent never also gets outreach

A leads-only agent cannot use a group that has a campaign or an agent with outreach, and an agent with outreach cannot use a leads-only agent's group. Agents with the same group name otherwise share the group.
