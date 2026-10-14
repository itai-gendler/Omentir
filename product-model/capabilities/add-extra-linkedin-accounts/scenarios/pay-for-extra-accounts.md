---
kind: primary
routes:
  web: Web app
steps:
- text: The User picks how many extra LinkedIn accounts they want
  kind: actor
  actor: user
  entities: [{entity: user, effect: reads, facts: [Extra LinkedIn accounts]}, {entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The User pays for them at checkout and comes back
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product records the extra LinkedIn accounts and raises the User's account limit
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Extra LinkedIn accounts]}, {entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Pay for extra accounts

## Trigger

The User wants to send from more LinkedIn accounts.

## Outcome

The User can connect as many more LinkedIn accounts as they paid for.
