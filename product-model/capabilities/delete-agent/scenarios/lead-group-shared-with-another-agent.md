---
kind: edge
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
- text: Another agent still fills the same lead group
  kind: condition
  entities: [{entity: lead-group, effect: reads, facts: [Name]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product keeps the lead group, its campaigns and leads for that agent
  kind: product
  entities: [{entity: campaign, effect: reads, facts: []}, {entity: agent, effect: reads, facts: []}, {entity: lead-group, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Lead group shared with another agent

## Trigger

Two agents share a group name.

## Outcome

Only the deleted agent's own outreach stops.
