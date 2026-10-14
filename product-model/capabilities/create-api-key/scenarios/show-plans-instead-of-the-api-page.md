---
kind: validation
routes:
  web: Web app
steps:
- text: The User opens the API page
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::api-keys'}
- text: The User has no active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::api-keys'}
- text: The Product sends the User to the plans
  kind: product
  entities: [{entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::plans'}
---

# Show plans instead of the api page

## Trigger

An unsubscribed User wants an API key.

## Outcome

No key is created.
