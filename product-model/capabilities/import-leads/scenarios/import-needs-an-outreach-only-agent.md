---
kind: validation
routes:
  agent: Agent API
steps:
- text: The Connected AI app sends a CSV for an agent that is not Outreach only
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Type]}]
  contexts:
    agent: {place: agent-api}
- text: The Product refuses the import
  kind: product
  entities: []
  contexts:
    agent: {place: agent-api}
---

# Import needs an outreach only agent

## Trigger

The AI app picks the wrong agent.

## Outcome

No lead is added.
