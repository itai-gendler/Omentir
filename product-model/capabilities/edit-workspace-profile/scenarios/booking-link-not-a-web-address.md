---
kind: validation
routes:
  web: Web app
steps:
- text: The User enters a demo booking link
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
- text: The link is not a valid web address
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
- text: The Product keeps the previous profile and says the link is not valid
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Demo booking link]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
---

# Booking link not a web address

## Trigger

The User types something that is not a link.

## Outcome

Nothing is saved; the User can correct the link.
