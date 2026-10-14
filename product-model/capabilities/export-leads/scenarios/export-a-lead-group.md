---
kind: primary
routes:
  web: Web app
steps:
- text: The User exports a lead group as CSV
  kind: actor
  actor: user
  entities: [{entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product builds the CSV of the group's leads, with dates on the workspace's calendar
  kind: product
  entities: [{entity: lead, effect: reads, facts: [Name, Headline, Company, Location, LinkedIn profile, Fit score, Score reasons, Summary, Engagement]}, {entity: workspace, effect: reads, facts: [Time zone]}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Export a lead group

## Trigger

The User wants the leads in another tool.

## Outcome

The User downloads the group's leads.
