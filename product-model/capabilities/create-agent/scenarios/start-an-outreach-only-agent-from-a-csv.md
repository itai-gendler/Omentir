---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Outreach only, uploads a CSV of LinkedIn profiles and sets the sequence
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
- text: The Product creates the agent without discovery
  kind: product
  actor: user
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Sending account]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product adds each profile as a lead with a fit score of 100; a person another agent already found keeps that agent as source
  kind: product
  actor: user
  entities: [{entity: lead, effect: creates, to: New, facts: [Name, LinkedIn profile, Headline, Company, Fit score, Score reasons, Summary, Lead reason, Source agent]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the campaign on the lead group
  kind: product
  actor: user
  entities: [{entity: campaign, effect: creates, facts: [Name, Steps, Send window, When a lead replies, Booking link, Email me when a lead replies, Goal, Message tone, Sending account]}, {entity: lead-group, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Start an outreach only agent from a csv

## Trigger

The User already has a list of people to contact.

## Outcome

The campaign contacts the imported people; the agent never looks for new leads.
