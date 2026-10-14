---
kind: primary
routes:
  web: Web app
steps:
- text: 'The User picks a period on Overview: 7 days, 30 days, 3 months or this month'
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The Product counts hot opportunities, invitations sent, messages sent and the pipeline value at the workspace's deal size for that period
  kind: product
  entities: [{entity: conversation, effect: reads, facts: [Reply intent, Meeting booked at]}, {entity: workspace, effect: reads, facts: [Deal size]}, {entity: lead-outreach, effect: reads, facts: [Invitation sent at]}]
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The User reads the hot opportunities with each lead's fit score
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name, Headline, Company, Fit score]}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Read results for a period

## Trigger

The User wants to see how outreach is going.

## Outcome

The User sees the period's results and the leads showing interest.
