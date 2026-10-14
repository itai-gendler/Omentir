---
kind: primary
routes:
  web: Web app
steps:
- text: The User enters an average deal size on Overview
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The Product saves the deal size and values the pipeline with it
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Deal size]}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Set the average deal size

## Trigger

The User wants the pipeline shown in money.

## Outcome

The pipeline on Overview is valued at the new deal size.
