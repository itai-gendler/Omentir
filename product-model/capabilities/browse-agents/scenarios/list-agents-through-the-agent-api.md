---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists the workspace's agents
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Name, Type, Leads only, Next run, Last run]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# List agents through the agent api

## Trigger

The User asks their AI app what their agents are doing.

## Outcome

The AI app has every agent with its status.
