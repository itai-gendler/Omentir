---
kind: primary
routes:
  web: Web app
steps:
- text: The User switches an agent off
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product pauses the agent
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, from: Active, to: Paused, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Switch an agent off

## Trigger

The User wants a break in outreach.

## Outcome

Nothing is found or sent for this agent's leads until it is resumed.
