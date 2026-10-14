---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app sends changes to an agent, optionally asking to set up outreach
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product saves the agent; attaching outreach to a leads-only agent turns leads only off and creates its campaign
  kind: product
  actor: ai-agent
  entities: [{entity: agent, effect: changes, facts: [Name, Prospect description, Job titles, Industries, Locations, Keywords, Leads only]}, {entity: campaign, effect: creates, facts: [Name, Steps, Send window, When a lead replies, Booking link, Email me when a lead replies, Goal, Message tone, Sending account]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Edit an agent through the agent api

## Trigger

The User asks their AI app to adjust an agent or start outreach on it.

## Outcome

The agent works the new way.
