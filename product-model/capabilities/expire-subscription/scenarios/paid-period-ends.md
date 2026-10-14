---
kind: primary
routes:
  web: Web app
steps:
- text: The User's paid period has ended without renewal
  kind: condition
  unattended: true
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product marks the subscription expired and removes the extra LinkedIn accounts
  kind: product
  entities: [{entity: user, effect: changes, facts: [Subscription status, Extra LinkedIn accounts]}, {entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product disconnects every LinkedIn account of the User's workspaces
  kind: product
  entities: [{entity: linkedin-account, effect: changes, from: Connected, to: Disconnected, facts: []}, {entity: user, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Paid period ends

## Trigger

Billing lapses.

## Outcome

Nothing is found or sent for the User until they subscribe and connect LinkedIn again.
