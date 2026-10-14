---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app pauses an agent
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product pauses the agent
  kind: product
  actor: ai-agent
  entities: [{entity: agent, effect: changes, from: Active, to: Paused, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Pause through the agent api

## Trigger

The User asks their AI app to stop an agent.

## Outcome

The agent is paused.
