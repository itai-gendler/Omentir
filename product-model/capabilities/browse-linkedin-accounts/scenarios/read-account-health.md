---
kind: primary
routes:
  web: Web app
steps:
- text: The User reads the connected LinkedIn accounts and their health in Settings
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name, Photo, Connected on, Health]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Read account health

## Trigger

The User wants to know whether LinkedIn may restrict an account.

## Outcome

The User sees how close each account is to LinkedIn's limits.
