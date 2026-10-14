---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Leads + outreach and describes the prospects, the group and the sending LinkedIn account
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The User sets the sequence, written by AI or by themselves, the goal, the tone, the send window and what happens when a lead replies, then reviews and launches
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the lead group, or uses the existing group of that name
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: creates, facts: [Name, Lead count]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the agent, active and due to look for leads now
  kind: product
  actor: user
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Prospect description, Job titles, Industries, Locations, Keywords, Sending account, Leads only, Daily run time, Next run]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the campaign on the lead group
  kind: product
  actor: user
  entities: [{entity: campaign, effect: creates, facts: [Name, Steps, Send window, When a lead replies, Booking link, Email me when a lead replies, Goal, Message tone, Sending account]}, {entity: lead-group, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product opens AI Agents
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Start a leads and outreach agent

## Trigger

The User wants Omentir to find buyers and contact them.

## Outcome

The agent finds leads and its campaign contacts each one as they arrive.

## Edge cases

- A sequence written by AI starts with a bare invitation; a note is attached only when the User writes one.
