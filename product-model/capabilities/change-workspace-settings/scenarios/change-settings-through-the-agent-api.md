---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app sends new limits or a new time zone
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent: {place: agent-api}
- text: The Product saves them
  kind: product
  actor: ai-agent
  entities: [{entity: workspace, effect: changes, facts: [Time zone, Daily invite limit, Daily message limit, First message delay]}]
  contexts:
    agent: {place: agent-api}
---

# Change settings through the agent api

## Trigger

The User asks their AI app to slow outreach down.

## Outcome

The workspace uses the new settings.
