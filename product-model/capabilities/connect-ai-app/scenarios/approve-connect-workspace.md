---
kind: primary
routes:
  web: Web app
steps:
- text: The User reviews the AI app's request and picks the workspace it may use
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::connect-ai-app'}
- text: The User approves Connect workspace
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::connect-ai-app'}
- text: The Product issues an API key named after the AI app for that workspace and hands it to the app
  kind: product
  actor: user
  entities: [{entity: api-key, effect: creates, to: Active, facts: [Label, Key prefix, Created]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::connect-ai-app'}
---

# Approve connect workspace

## Trigger

The User adds Omentir's connector to their AI app.

## Outcome

The AI app can call the agent API in the chosen workspace; its key is listed on the API page.
