---
kind: edge
routes:
  web: Web app
steps:
- text: The User asks AI to suggest who the agent should look for
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The AI model does not answer
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product fills the setup from the company profile's buyer profile instead
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Buyer profile]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Suggestion from the profile alone

## Trigger

The model is unavailable.

## Outcome

The setup is still pre-filled and the User can continue.
