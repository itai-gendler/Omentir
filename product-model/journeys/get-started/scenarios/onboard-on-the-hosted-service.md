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
- text: The User answers the onboarding questions
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::onboarding'}
  capability: answer-onboarding-questions
- text: The Product saves the answers and shows the plans
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Onboarding answers]}]
  contexts:
    web: {place: 'web-app::app::onboarding'}
  capability: answer-onboarding-questions
- text: The User chooses a plan and pays at checkout
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::plans'}
  capability: subscribe
- text: The Product marks the subscription active and opens Overview
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Subscription status, Plan]}]
  contexts:
    web: {place: 'web-app::app::overview'}
  capability: subscribe
---

# Onboard on the hosted service

## Trigger

A new User signs up.

## Outcome

The User lands on Overview with the setup checklist's subscription step done.
