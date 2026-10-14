---
kind: primary
routes:
  web: Web app
steps:
- text: An active agent's daily run time has come
  kind: condition
  unattended: true
  entities: [{entity: agent, effect: reads, facts: [Daily run time, Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product marks the agent running
  kind: product
  entities: [{entity: agent, effect: changes, from: Active, to: Running, facts: [Last run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product searches LinkedIn for people matching the agent's job titles, industries, keywords and locations, skipping anyone already a lead in the workspace or rejected before
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Job titles, Industries, Keywords, Locations, Sending account]}, {entity: lead, effect: reads, facts: [LinkedIn profile]}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product asks the AI model to score each person against the company profile and saves those scoring 65 or more as new leads in the agent's lead group
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description, Buyer profile]}, {entity: lead, effect: creates, to: New, facts: [Name, Headline, Company, Location, LinkedIn profile, Photo, Summary, Fit score, Score reasons, Lead reason, Source agent]}, {entity: lead-group, effect: changes, facts: [Lead count]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product makes the agent active again
  kind: product
  entities: [{entity: agent, effect: changes, from: Running, to: Active, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Find and score new leads

## Trigger

The agent's daily run time.

## Outcome

New fitting leads are in the agent's lead group, ready for its campaign.

## Edge cases

- A run that saves fewer than its daily target tries again 30 minutes later, up to four runs a day.
- People outside the agent's locations are never saved, whatever their score.
