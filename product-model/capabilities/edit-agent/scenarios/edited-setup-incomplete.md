---
kind: validation
routes:
  web: Web app
steps:
- text: The User saves an agent with part of its targeting removed
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product refuses and names the missing fields
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Edited setup incomplete

## Trigger

The User clears a required field.

## Outcome

The agent is unchanged.
