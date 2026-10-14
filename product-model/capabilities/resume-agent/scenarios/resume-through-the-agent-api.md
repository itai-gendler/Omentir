---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app resumes an agent
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product makes the agent active and due now
  kind: product
  actor: ai-agent
  entities: [{entity: agent, effect: changes, from: Paused, to: Active, facts: [Next run]}]
  contexts:
    agent: {place: agent-api}
---

# Resume through the agent api

## Trigger

The User asks their AI app to restart an agent.

## Outcome

The agent runs again.
