---
kind: edge
routes:
  web: Web app
steps:
- text: An active agent's run time has come
  kind: condition
  unattended: true
  entities: [{entity: agent, effect: reads, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: No connected LinkedIn account can be used
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product marks the agent as Error, records why, and tries again at its next daily run
  kind: product
  entities: [{entity: agent, effect: changes, from: Active, to: Error, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# No linkedin account to search with

## Trigger

LinkedIn was disconnected.

## Outcome

The agent shows an error until LinkedIn is connected or it is resumed.

## Edge cases

- A search that fails partway marks the agent as Error too; leads already saved stay.
