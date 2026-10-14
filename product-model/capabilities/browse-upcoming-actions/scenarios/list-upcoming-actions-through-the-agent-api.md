---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists the upcoming actions, optionally for one agent or lead
  kind: actor
  actor: ai-agent
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Prepared message, Blocked reason]}, {entity: lead, effect: reads, facts: [Name]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# List upcoming actions through the agent api

## Trigger

The User asks their AI app what goes out today.

## Outcome

The AI app has the exact send times.
