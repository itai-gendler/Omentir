---
kind: primary
routes:
  web: Web app
steps:
- text: The User continues from the example buyers on a self-hosted install
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The Product records onboarding as done without questions and opens Overview
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Onboarding answers]}]
  contexts:
    web: {place: 'web-app::app::onboarding'}
---

# Self hosted onboarding skips the questions

## Trigger

The operator of a self-hosted install finishes onboarding.

## Outcome

Overview opens; there is no plan to choose.
