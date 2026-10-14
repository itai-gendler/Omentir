---
kind: primary
routes:
  web: Web app
steps:
- text: The Visitor creates an Omentir account
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web-app::sign-in::sign-up'}
- text: The Product creates the new person's first Workspace with the default sending settings
  kind: product
  entities: [{entity: workspace, effect: creates, facts: [Name, Daily invite limit, Daily message limit, First message delay, Daily summary, Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::sign-in::sign-up'}
---

# Create an account

## Trigger

A Visitor wants to start using the hosted service.

## Outcome

The Visitor is signed in as a User with one empty Workspace and is taken to onboarding.
