---
kind: validation
routes:
  web: Web app
steps:
- text: The User saves a message over 1,900 characters
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product refuses it as too long
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Message too long

## Trigger

The User writes too much.

## Outcome

The previous message stays.
