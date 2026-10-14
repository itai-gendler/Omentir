---
kind: validation
routes:
  web: Web app
steps:
- text: The User launches an agent with outreach and a group name
  kind: actor
  actor: user
  entities: [{entity: lead-group, effect: reads, facts: [Name]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: A leads-only agent already fills the group of that name
  kind: condition
  entities: [{entity: agent, effect: reads, facts: [Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product refuses and asks for a different group name
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Group belongs to a leads only agent

## Trigger

The User reuses the name of a leads-only group.

## Outcome

No agent is created; those people stay uncontacted.
