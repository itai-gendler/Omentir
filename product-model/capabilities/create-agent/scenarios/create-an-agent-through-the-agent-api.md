---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks for an agent with a type, targeting or competitor pages, a group name and, optionally, outreach settings
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product creates the lead group, or uses the existing group of that name
  kind: product
  actor: ai-agent
  entities: [{entity: lead-group, effect: creates, facts: [Name, Lead count]}]
  contexts:
    agent: {place: agent-api}
- text: The Product creates the agent, leads only unless outreach was asked for or the type needs it
  kind: product
  actor: ai-agent
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Prospect description, Job titles, Industries, Locations, Keywords, Sending account, Leads only, Daily run time, Next run]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product creates the campaign when the agent has outreach
  kind: product
  actor: ai-agent
  entities: [{entity: campaign, effect: creates, facts: [Name, Steps, Send window, When a lead replies, Booking link, Email me when a lead replies, Goal, Message tone, Sending account]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Create an agent through the agent api

## Trigger

The User asks their AI app to start an agent.

## Outcome

The AI app gets the agent, its lead group and when discovery runs.
