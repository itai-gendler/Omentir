---
kind: validation
routes:
  web: Web app
steps:
- text: The Visitor enters a password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
- text: The password does not match the configured access password
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
- text: The Product refuses the sign-in and says the password is wrong
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
---

# Wrong access password refused

## Trigger

A Visitor of a self-hosted install with an access password enters the wrong one.

## Outcome

The Visitor stays signed out on the sign-in page.
