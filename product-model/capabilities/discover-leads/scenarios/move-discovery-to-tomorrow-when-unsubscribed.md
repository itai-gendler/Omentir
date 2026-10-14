---
kind: edge
routes:
  web: Web app
steps:
- text: An active agent's run time has come
  kind: condition
  unattended: true
  entities: [{entity: agent, effect: reads, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The User has no active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product skips the run and moves it to the next day
  kind: product
  entities: [{entity: agent, effect: changes, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Move discovery to tomorrow when unsubscribed

## Trigger

The subscription lapsed.

## Outcome

Nothing is searched until the User subscribes again.
