---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Steal Customers and adds competitor company pages and, optionally, founder or employee profiles
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The company profile has a company name, description or pain points
  kind: condition
  entities: [{entity: workspace, effect: reads, facts: [Company name, Description, Pain points]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the lead group, or uses the existing group of that name
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: creates, facts: [Name, Lead count]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the agent with its targeting taken from the company profile
  kind: product
  actor: user
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Prospect description, Competitor pages, Sending account, Daily run time, Next run]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the campaign with AI-written messages
  kind: product
  actor: user
  entities: [{entity: campaign, effect: creates, facts: [Name, Steps, Send window, When a lead replies, Booking link, Email me when a lead replies, Goal, Message tone, Sending account]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Start a steal customers agent

## Trigger

The User wants the people already engaging with competitors.

## Outcome

The agent watches the competitor pages and its campaign reaches out using each person's post and comment.
