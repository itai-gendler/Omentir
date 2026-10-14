---
kind: primary
routes:
  web: Web app
steps:
- text: The User picks a lead group or All contacts and searches
  kind: actor
  actor: user
  entities: [{entity: lead-group, effect: reads, facts: [Name, Lead count]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The User opens a lead to see why they fit and what surfaced them
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name, Headline, Company, Location, LinkedIn profile, Summary, Fit score, Score reasons, Lead reason, Engagement]}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Browse a lead group

## Trigger

The User reviews what agents found.

## Outcome

The User knows who each lead is and why they were picked.
