---
kind: edge
routes:
  web: Web app
steps:
- text: The User opens Overview
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The workspace lacks an active subscription, a connected LinkedIn account, a demo booking link or an agent
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}, {entity: workspace, effect: reads, facts: [Demo booking link]}, {entity: linkedin-account, effect: reads, facts: []}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The Product shows the setup checklist with each step done or still to do, instead of results
  kind: product
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Setup checklist before results

## Trigger

A User opens a workspace that is not set up yet.

## Outcome

The User sees which of the four setup steps remain.
