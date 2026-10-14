---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app marks a lead's follow-up done
  kind: actor
  actor: ai-agent
  entities: [{entity: conversation, effect: reads, facts: [Category]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product records it
  kind: product
  actor: ai-agent
  entities: [{entity: conversation, effect: changes, facts: [Follow-up done at]}]
  contexts:
    agent: {place: agent-api}
---

# Mark done through the agent api

## Trigger

The User's AI app followed up.

## Outcome

The follow-up is cleared.
