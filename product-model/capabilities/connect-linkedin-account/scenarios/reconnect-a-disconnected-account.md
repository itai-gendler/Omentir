---
kind: primary
routes:
  web: Web app
steps:
- text: The workspace's LinkedIn account was disconnected
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The User chooses to connect LinkedIn again
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The LinkedIn connection service reports the account reconnected
  kind: actor
  actor: linkedin-provider
  entities: []
  contexts:
    web: {place: linkedin-events}
- text: The Product marks the LinkedIn account connected again
  kind: product
  entities: [{entity: linkedin-account, effect: changes, from: Disconnected, to: Connected, facts: [Display name, Photo]}]
  contexts:
    web: {place: linkedin-events}
---

# Reconnect a disconnected account

## Trigger

The LinkedIn session ended or the User disconnected it.

## Outcome

The same LinkedIn account is connected again with its history.
