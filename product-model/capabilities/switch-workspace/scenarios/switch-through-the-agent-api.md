---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists the User's workspaces and asks to switch to one
  kind: actor
  actor: ai-agent
  entities: [{entity: workspace, effect: reads, facts: [Name]}, {entity: user, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product moves the API key to that workspace, so later calls work there
  kind: product
  actor: ai-agent
  entities: [{entity: api-key, effect: changes, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Switch through the agent api

## Trigger

The User tells their AI app to work on another company.

## Outcome

The key now works in the chosen workspace.
