---
kind: primary
routes:
  web: Web app
steps:
- text: The User names a new key and creates it
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::api-keys'}
- text: The Product creates the API key and shows it in full once, for the User to copy
  kind: product
  actor: user
  entities: [{entity: api-key, effect: creates, to: Active, facts: [Label, Key prefix, Created]}]
  contexts:
    web: {place: 'web-app::app::api-keys'}
---

# Create a key

## Trigger

The User wants to connect a coding agent or script.

## Outcome

The User has a key for the agent API; later only its prefix is shown.
