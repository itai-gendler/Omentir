---
kind: edge
routes:
  web: Web app
steps:
- text: The User opens Messages
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::messages'}
- text: No LinkedIn account is connected
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product asks the User to connect LinkedIn on Overview
  kind: product
  entities: [{entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Messages before linkedin is connected

## Trigger

A workspace without LinkedIn.

## Outcome

The User is pointed at connecting LinkedIn.
