---
kind: validation
routes:
  web: Web app
steps:
- text: The User launches an agent with a prospect description, job titles, industries, locations or keywords missing
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product refuses to create the agent and names the missing fields
  kind: product
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Agent setup incomplete

## Trigger

The User skips part of the targeting.

## Outcome

No agent is created.
