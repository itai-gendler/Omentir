---
kind: primary
routes:
  web: Web app
steps:
- text: The User picks another of their workspaces in the switcher
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app'}
- text: The Product makes it the active workspace for every page
  kind: product
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app'}
---

# Switch in the app

## Trigger

The User wants to work on another company.

## Outcome

Every page shows the chosen workspace.
