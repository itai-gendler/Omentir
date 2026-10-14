---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app stops outreach to a lead
  kind: actor
  actor: ai-agent
  entities: [{entity: lead, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product stops the lead's outreach
  kind: product
  actor: ai-agent
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: changes, from: New, to: Stopped, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Stop through the agent api

## Trigger

The User tells their AI app to leave someone alone.

## Outcome

The lead is not contacted.
