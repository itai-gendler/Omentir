---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Leads only on an agent and confirms
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name, Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product marks the agent leads only
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, facts: [Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Make an agent leads only

## Trigger

The User wants to contact this agent's leads personally.

## Outcome

From the next automation run nobody this agent found is contacted automatically.
