---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Disconnect on a LinkedIn account
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product ends the session at the LinkedIn connection service and marks the account disconnected
  kind: product
  actor: user
  entities: [{entity: linkedin-provider, effect: reads, facts: []}, {entity: linkedin-account, effect: changes, from: Connected, to: Disconnected, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Disconnect an account

## Trigger

The User stops using a LinkedIn account with Omentir.

## Outcome

Nothing more is sent from that LinkedIn account.
