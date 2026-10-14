---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks for a suggested agent setup
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product returns a drafted prospect description and targeting from the company profile
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description, Buyer profile]}]
  contexts:
    agent: {place: agent-api}
---

# Draft through the agent api

## Trigger

The AI app prepares an agent for the User.

## Outcome

The AI app has a starting point for a new agent.
