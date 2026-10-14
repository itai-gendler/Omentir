---
kind: primary
routes:
  web: Web app
steps:
- text: The User answers how they heard of Omentir, their role, company size and goal
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The Product saves the answers and moves onboarding on to choosing a plan
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Onboarding answers]}]
  contexts:
    web: {place: 'web-app::app::onboarding'}
---

# Answer the questions

## Trigger

The User has seen the example buyers.

## Outcome

Onboarding shows the plans.
