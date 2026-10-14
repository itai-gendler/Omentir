---
kind: validation
routes:
  web: Web app
steps:
- text: The User sends a reply
  kind: actor
  actor: user
  entities: [{entity: linkedin-chat, effect: reads, facts: [Participant]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The chat does not belong to the chosen LinkedIn account, or that account is not usable from this workspace
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product refuses to send
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Chat not on that account

## Trigger

The User picks the wrong sending account.

## Outcome

Nothing is sent from the wrong identity.

## Edge cases

- An attachment over 15 MB is refused before anything is sent.
