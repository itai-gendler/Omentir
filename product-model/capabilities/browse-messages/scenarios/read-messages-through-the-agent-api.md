---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists the inbox and conversations and reads a chat's messages
  kind: actor
  actor: ai-agent
  entities: [{entity: linkedin-chat, effect: reads, facts: [Participant, Messages]}, {entity: conversation, effect: reads, facts: [Messages, Reply intent]}]
  contexts:
    agent: {place: agent-api}
---

# Read messages through the agent api

## Trigger

The User asks their AI app who replied.

## Outcome

The AI app has the conversations.
