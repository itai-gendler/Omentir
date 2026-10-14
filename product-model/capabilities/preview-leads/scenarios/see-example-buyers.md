---
kind: primary
routes:
  web: Web app
steps:
- text: The User reaches the example buyers step of onboarding
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
- text: The Product asks the AI model for example buyers matching the company profile and shows them without saving them
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description, Buyer profile]}]
  contexts:
    web: {place: 'web-app::app::onboarding'}
---

# See example buyers

## Trigger

The company profile was just filled from the website.

## Outcome

The User sees example buyers and can continue.
