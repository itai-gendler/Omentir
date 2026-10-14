---
kind: primary
routes:
  web: Web app
steps:
- text: The User switches an agent in error back on
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product clears the error and makes the agent active and due now
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, from: Error, to: Active, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Resume after an error

## Trigger

The User fixed what made the last run fail.

## Outcome

The agent tries again right away.
