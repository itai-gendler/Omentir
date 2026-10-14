---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Allow outreach on a leads-only agent and confirms
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name, Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product turns leads only off for the agent
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, facts: [Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Allow outreach again

## Trigger

The User wants the agent's leads contacted after all.

## Outcome

Campaigns on its lead group may contact the people it finds; if it has no campaign yet the User edits it to add one.
