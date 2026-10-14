---
kind: edge
routes:
  web: Web app
steps:
- text: The User reaches the example buyers step of onboarding
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The AI model finds no example buyers in time
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The Product says no examples were found and offers to try again
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
---

# No example buyers found

## Trigger

The model is slow or unavailable.

## Outcome

The User can retry; nothing is saved.
