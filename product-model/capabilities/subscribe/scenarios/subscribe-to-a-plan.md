---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses a plan
  kind: actor
  actor: user
  entities: [{entity: user, effect: reads, facts: [Plan]}]
  contexts:
    web: {place: 'web-app::app::plans'}
- text: The Product sends the User to checkout with their email filled in
  kind: product
  entities: [{entity: user, effect: reads, facts: [Email]}]
  contexts:
    web: {place: 'web-app::app::plans'}
- text: The User pays at checkout and comes back
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::plans'}
- text: The Product confirms the payment with the billing service and marks the subscription active on every workspace the User owns
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Subscription status, Plan]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Subscribe to a plan

## Trigger

The User wants agents to start finding and contacting people.

## Outcome

The subscription is active; Overview moves on to the next setup step.
