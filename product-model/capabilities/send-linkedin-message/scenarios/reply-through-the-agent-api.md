---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app replies to a lead or in a chat
  kind: actor
  actor: ai-agent
  entities: [{entity: linkedin-chat, effect: reads, facts: [Participant]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product sends it from the owning account and records it
  kind: product
  actor: ai-agent
  entities: [{entity: linkedin-chat, effect: changes, facts: [Messages]}, {entity: conversation, effect: changes, facts: [Messages]}]
  contexts:
    agent: {place: agent-api}
---

# Reply through the agent api

## Trigger

The User asks their AI app to answer someone.

## Outcome

The reply is sent.
