---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks for the workspace's results for a period
  kind: actor
  actor: ai-agent
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product returns the counts of leads found, people contacted, replies and meetings booked
  kind: product
  entities: [{entity: lead, effect: reads, facts: []}, {entity: conversation, effect: reads, facts: [Reply intent, Meeting booked at]}]
  contexts:
    agent: {place: agent-api}
---

# Read results through the agent api

## Trigger

The User asks their AI app how outreach is going.

## Outcome

The AI app has the period's numbers.
