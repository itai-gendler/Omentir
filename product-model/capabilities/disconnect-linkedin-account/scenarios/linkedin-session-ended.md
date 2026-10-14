---
kind: edge
routes:
  web: Web app
steps:
- text: The LinkedIn connection service no longer holds the account's session
  kind: condition
  unattended: true
  entities: [{entity: linkedin-provider, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The Product marks the LinkedIn account disconnected, and Overview asks the User to connect it again
  kind: product
  entities: [{entity: linkedin-account, effect: changes, from: Connected, to: Disconnected, facts: []}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Linkedin session ended

## Trigger

LinkedIn signed the account out.

## Outcome

The User is asked to reconnect.
