---
kind: validation
routes:
  web: Web app
steps:
- text: The User chooses New workspace without a landing page
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app'}
- text: The Product asks for the landing page and creates nothing
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app'}
---

# New workspace needs a landing page

## Trigger

The User leaves the landing page empty.

## Outcome

No workspace is created.
