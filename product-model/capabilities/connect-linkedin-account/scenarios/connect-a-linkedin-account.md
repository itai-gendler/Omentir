---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Connect account
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product sends the User to sign in to LinkedIn through the LinkedIn connection service
  kind: product
  entities: [{entity: linkedin-provider, effect: reads, facts: []}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The LinkedIn connection service reports the newly connected account
  kind: actor
  actor: linkedin-provider
  entities: []
  contexts:
    web: {place: linkedin-events}
- text: The Product checks the account exists at the service and saves it as a connected LinkedIn account of the workspace
  kind: product
  entities: [{entity: linkedin-account, effect: creates, to: Connected, facts: [Display name, Photo, Connected on]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: linkedin-events}
- text: The Product returns the User to Overview with the account connected
  kind: product
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Connect a linkedin account

## Trigger

The User sets up LinkedIn so agents can search and send.

## Outcome

The LinkedIn account is connected and usable from every workspace the User owns.
