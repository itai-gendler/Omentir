---
domain: leads
relations:
- entity: agent
  verb: is filled by
  cardinality: one-to-many
- entity: lead
  verb: holds
  cardinality: one-to-many
- entity: campaign
  verb: is contacted by
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Group
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createOrGetGroup
---

# Lead group

The named list an agent fills with the leads it finds, and that campaigns contact. A lead belongs to one lead group.

## Information kept

- **Name** — the group's name; agents with the same group name share it
- **Lead count** — how many leads it holds
