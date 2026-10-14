---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app deletes an agent
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product stops the agent's outreach and deletes the agent
  kind: product
  actor: ai-agent
  entities: [{entity: agent, effect: removes, from: Active}]
  contexts:
    agent: {place: agent-api}
- text: The Product deletes the agent's lead group too, unless another agent fills it
  kind: product
  actor: ai-agent
  entities: [{entity: lead-group, effect: removes}, {entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Delete through the agent api

## Trigger

The User asks their AI app to remove an agent.

## Outcome

The agent is gone.
