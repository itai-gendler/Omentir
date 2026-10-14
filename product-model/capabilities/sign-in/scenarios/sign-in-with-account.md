---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor signs in with their Omentir account
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
- text: The Product signs the Visitor in and opens the page they were going to, or Overview
  kind: product
  entities: [{entity: visitor, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::sign-in::sign-in'}
---

# Sign in with account

## Trigger

A Visitor opens the hosted service and is not signed in.

## Outcome

The Visitor is signed in as a User and lands where they were going.
