---
kind: primary
routes:
  web: Web app
steps:
- text: The User revokes an API key
  kind: actor
  actor: user
  entities: [{entity: api-key, effect: reads, facts: [Label, Key prefix]}]
  contexts:
    web: {place: 'web-app::app::api-keys'}
- text: The Product revokes it; calls with it are refused from then on
  kind: product
  actor: user
  entities: [{entity: api-key, effect: changes, from: Active, to: Revoked, facts: []}]
  contexts:
    web: {place: 'web-app::app::api-keys'}
---

# Revoke a key

## Trigger

A key leaked or an AI app should lose access.

## Outcome

The key no longer works.
