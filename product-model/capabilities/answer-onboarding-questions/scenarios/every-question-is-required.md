---
kind: validation
routes:
  web: Web app
steps:
- text: The User submits the questions with one left empty
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The Product asks for every answer and saves nothing
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
---

# Every question is required

## Trigger

The User skips a question.

## Outcome

The User stays on the questions.
