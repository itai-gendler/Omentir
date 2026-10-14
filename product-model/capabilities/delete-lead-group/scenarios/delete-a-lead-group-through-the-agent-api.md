---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app deletes an unused lead group
  kind: actor
  actor: ai-agent
  entities: [{entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product deletes the group with its leads
  kind: product
  actor: ai-agent
  entities: [{entity: lead-group, effect: removes}, {entity: lead, effect: removes, from: New, with: lead-group}]
  contexts:
    agent: {place: agent-api}
---

# Delete a lead group through the agent api

## Trigger

The User asks their AI app to clean up.

## Outcome

The group is gone.
