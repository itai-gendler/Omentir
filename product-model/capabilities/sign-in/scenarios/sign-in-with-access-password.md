---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor enters the access password set by the instance's operator
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
- text: The Product checks the password and signs the Visitor in with an expiring session
  kind: product
  entities: [{entity: visitor, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
---

# Sign in with access password

## Trigger

A Visitor opens a self-hosted install that has an access password.

## Outcome

The Visitor is signed in as the install's User and lands where they were going.

## Edge cases

- Too many wrong passwords from one address are refused for a while with "Too many attempts".
