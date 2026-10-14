---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Stop outreach for a lead and confirms
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product stops the lead's outreach and marks the lead stopped
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: changes, from: New, to: Stopped, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Stop a new lead

## Trigger

The User does not want this person contacted.

## Outcome

Nothing is ever sent to the lead automatically.
