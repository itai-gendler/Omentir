---
kind: validation
routes:
  web: Web app
steps:
- text: The User connects a LinkedIn account
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The LinkedIn connection service reports the account
  kind: actor
  actor: linkedin-provider
  entities: []
  contexts:
    web: {place: linkedin-events}
- text: That LinkedIn account is already connected to another person's workspace
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: linkedin-events}
- text: The Product refuses to connect it here
  kind: product
  entities: []
  contexts:
    web: {place: linkedin-events}
---

# Linkedin account belongs to someone else

## Trigger

Two people try to use the same LinkedIn account.

## Outcome

The LinkedIn account stays with its first owner.
