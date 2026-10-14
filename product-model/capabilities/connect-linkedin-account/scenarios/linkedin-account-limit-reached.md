---
kind: validation
routes:
  web: Web app
steps:
- text: The User connects another LinkedIn account
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The LinkedIn connection service reports the new account
  kind: actor
  actor: linkedin-provider
  entities: []
  contexts:
    web: {place: linkedin-events}
- text: The User already has as many connected LinkedIn accounts as the plan and extra accounts allow
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Plan, Extra LinkedIn accounts]}, {entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: linkedin-events}
- text: The Product refuses to save the new account
  kind: product
  entities: []
  contexts:
    web: {place: linkedin-events}
---

# Linkedin account limit reached

## Trigger

The User is at their account limit.

## Outcome

The new account is not connected; the User can add extra LinkedIn accounts.
