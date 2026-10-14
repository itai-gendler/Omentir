---
kind: primary
routes:
  web: Web app
steps:
- text: Two hours have passed since a connected LinkedIn account of a subscribed workspace was last tidied
  kind: condition
  unattended: true
  entities: [{entity: linkedin-account, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: [Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product withdraws up to ten invitations pending longer than the setting, pausing between each, and records how many it withdrew
  kind: product
  entities: [{entity: linkedin-account, effect: reads, facts: [Health]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Withdraw old invitations

## Trigger

Invitations are piling up on an account.

## Outcome

Fewer pending invitations show in the account's health.
