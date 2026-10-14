---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists the workspace's LinkedIn accounts
  kind: actor
  actor: ai-agent
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# List accounts through the agent api

## Trigger

An AI app needs a sending account for a new agent.

## Outcome

The AI app knows which LinkedIn accounts it can use.
