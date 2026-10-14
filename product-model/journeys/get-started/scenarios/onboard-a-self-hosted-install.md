---
kind: primary
result: achieved
routes:
  web: Web app
steps:
- text: The User enters the company website
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
  capability: analyze-website
- text: The Product fills the company profile from the website
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Website, Company name, Description, Pain points, Pricing details, Selling points, Buyer profile]}]
  contexts:
    web: {place: 'web-app::app::onboarding'}
  capability: analyze-website
- text: The User looks at the example buyers and continues
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
  capability: preview-leads
- text: The Product records onboarding as done and opens Overview
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Onboarding answers]}]
  contexts:
    web: {place: 'web-app::app::overview'}
  capability: answer-onboarding-questions
---

# Onboard a self hosted install

## Trigger

The operator of a self-hosted install signs in for the first time.

## Outcome

Overview opens; a self-hosted install is always subscribed.
