---
kind: validation
routes:
  web: Web app
steps:
- text: The User enters a daily invite limit above 100 or a daily message limit above 200
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product refuses to save and keeps the previous settings
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Daily invite limit, Daily message limit]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Limit out of range

## Trigger

The User asks for more than Omentir allows.

## Outcome

The limits are unchanged.
