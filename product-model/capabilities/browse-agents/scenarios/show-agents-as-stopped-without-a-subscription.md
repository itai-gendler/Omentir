---
kind: edge
routes:
  web: Web app
steps:
- text: The User opens AI Agents
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The User has no active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product shows each agent as stopped with a link to renew
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Show agents as stopped without a subscription

## Trigger

The subscription lapsed.

## Outcome

The User sees their agents but nothing runs until they renew.
