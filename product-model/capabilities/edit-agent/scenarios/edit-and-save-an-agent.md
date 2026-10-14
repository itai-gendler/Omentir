---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens Edit on an agent, changes it and saves
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product saves the agent and renames its lead group in place
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, facts: [Name, Prospect description, Job titles, Industries, Locations, Keywords, Sending account]}, {entity: lead-group, effect: changes, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product applies the sequence, send window, reply handling, booking link and tone to every campaign on the lead group and moves leads mid-sequence to the matching step
  kind: product
  actor: user
  entities: [{entity: campaign, effect: changes, facts: [Steps, Send window, When a lead replies, Booking link, Message tone]}, {entity: lead-outreach, effect: changes, facts: [Current step]}, {entity: lead-group, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product opens AI Agents
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Edit and save an agent

## Trigger

The User wants the agent to look for different people or write differently.

## Outcome

From the next action on, the agent and its campaigns work the new way.
