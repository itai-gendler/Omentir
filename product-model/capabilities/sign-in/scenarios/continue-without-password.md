---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor chooses Continue to dashboard
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
- text: The Product signs the Visitor in without a password
  kind: product
  entities: [{entity: visitor, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
---

# Continue without password

## Trigger

A Visitor opens a self-hosted install whose operator allowed open access and set no password.

## Outcome

The Visitor is signed in as the install's User.
