---
kind: primary
routes:
  web: Web app
steps:
- text: A Steal Customers agent's daily run time has come
  kind: condition
  unattended: true
  entities: [{entity: agent, effect: reads, facts: [Daily run time, Competitor pages]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product marks the agent running
  kind: product
  entities: [{entity: agent, effect: changes, from: Active, to: Running, facts: [Last run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product reads recent posts by the competitor pages and their founders and employees, and the fresh comments and reactions on them
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Competitor pages, Sending account]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product scores each person against the company profile and saves likely buyers as leads with the post and comment that surfaced them
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description, Pain points, Buyer profile]}, {entity: lead, effect: creates, to: New, facts: [Name, Headline, Company, Location, LinkedIn profile, Photo, Summary, Fit score, Score reasons, Lead reason, Source agent, Engagement]}, {entity: lead-group, effect: changes, facts: [Lead count]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product makes the agent active again
  kind: product
  entities: [{entity: agent, effect: changes, from: Running, to: Active, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Find competitor commenters

## Trigger

The Steal Customers agent's daily run time.

## Outcome

People engaging with competitors are saved as leads with their engagement.
