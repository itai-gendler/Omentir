---
kind: validation
routes:
  web: Web app
steps:
- text: The User asks to make an Outreach only agent leads only
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Type]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product refuses, since that agent finds no leads
  kind: product
  entities: [{entity: agent, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Outreach only agent cannot be leads only

## Trigger

The User picks the wrong agent.

## Outcome

The agent is unchanged.
