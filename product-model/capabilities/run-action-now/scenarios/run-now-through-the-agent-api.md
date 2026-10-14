---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app runs a lead's next action now
  kind: actor
  actor: ai-agent
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product sends it right away
  kind: product
  actor: ai-agent
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Invitation sent, facts: [Current step, Invitation sent at, Next action at]}, {entity: lead, effect: changes, from: New, to: Invited, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Run now through the agent api

## Trigger

The User asks their AI app to push an action out.

## Outcome

The action is sent.
