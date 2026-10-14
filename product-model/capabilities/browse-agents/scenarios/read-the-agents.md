---
kind: primary
routes:
  web: Web app
steps:
- text: The User filters the agents by status and reads each one's type, lead group and next run
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name, Type, Leads only, Next run, Last run]}, {entity: lead-group, effect: reads, facts: [Name, Lead count]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product shows for each agent how many of its leads were contacted, accepted, messaged and replied
  kind: product
  entities: [{entity: lead, effect: reads, facts: [Source agent]}, {entity: lead-outreach, effect: reads, facts: [Invitation sent at]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Read the agents

## Trigger

The User checks on their agents.

## Outcome

The User sees every agent's progress.
