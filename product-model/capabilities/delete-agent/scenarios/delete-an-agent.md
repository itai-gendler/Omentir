---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes an agent and confirms
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product stops outreach to every lead the agent found and deletes the agent
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, from: Invitation sent, to: Stopped, facts: [Blocked reason]}, {entity: agent, effect: removes, from: Active}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product deletes the agent's lead group with its campaigns and leads, since no other agent fills it
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: removes}, {entity: campaign, effect: removes, with: lead-group}, {entity: lead, effect: removes, from: Invited, with: lead-group}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Delete an agent

## Trigger

The User is done with an agent.

## Outcome

The agent, its lead group, campaigns and leads are gone; activity totals on Overview keep their history.
