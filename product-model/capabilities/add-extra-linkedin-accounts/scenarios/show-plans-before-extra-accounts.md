---
kind: validation
routes:
  web: Web app
steps:
- text: The User asks for extra LinkedIn accounts
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The User has no active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product sends the User to the plans first
  kind: product
  entities: [{entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::plans'}
---

# Show plans before extra accounts

## Trigger

An unsubscribed User tries to add accounts.

## Outcome

Nothing is bought.
