---
kind: edge
routes:
  web: Web app
steps:
- text: Two hours have passed since a connected LinkedIn account was last tidied
  kind: condition
  unattended: true
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The workspace's invite withdrawal is 0
  kind: condition
  entities: [{entity: workspace, effect: reads, facts: [Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product withdraws nothing
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Invite withdrawal off

## Trigger

The User turned withdrawal off.

## Outcome

Pending invitations stay.
