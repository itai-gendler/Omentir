---
kind: edge
routes:
  web: Web app
steps:
- text: The User chooses a plan
  kind: actor
  actor: user
  entities: [{entity: user, effect: reads, facts: [Plan]}]
  contexts:
    web: {place: 'web-app::app::plans'}
- text: The billing service does not return a checkout
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::app::plans'}
- text: The Product says checkout failed to start
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::plans'}
---

# Checkout cannot start

## Trigger

The billing service is unavailable.

## Outcome

Nothing is charged and the subscription is unchanged.
