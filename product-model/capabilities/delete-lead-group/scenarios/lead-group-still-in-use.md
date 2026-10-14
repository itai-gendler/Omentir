---
kind: validation
routes:
  web: Web app
steps:
- text: The User deletes a lead group
  kind: actor
  actor: user
  entities: [{entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: An agent still fills the group, or a campaign contacts it
  kind: condition
  entities: [{entity: agent, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product refuses and asks the User to delete or reassign the agent or campaign first
  kind: product
  entities: [{entity: user, effect: reads, facts: []}, {entity: agent, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Lead group still in use

## Trigger

The User tries to delete an agent's group.

## Outcome

Nothing is deleted.
