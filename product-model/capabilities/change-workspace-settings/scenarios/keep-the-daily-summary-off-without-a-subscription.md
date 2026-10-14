---
kind: validation
routes:
  web: Web app
steps:
- text: The User turns the daily summary on and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The User has no active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product saves the other settings and keeps the daily summary off
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Time zone, Daily invite limit, Daily message limit, First message delay, Daily summary hour, Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Keep the daily summary off without a subscription

## Trigger

An unsubscribed User wants the summary.

## Outcome

No daily summary is sent.
