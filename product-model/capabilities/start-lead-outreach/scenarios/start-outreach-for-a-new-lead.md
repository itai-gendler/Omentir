---
kind: primary
routes:
  web: Web app
steps:
- text: A new lead is in the lead group of an active campaign
  kind: condition
  unattended: true
  entities: [{entity: lead, effect: reads, facts: [Source agent]}, {entity: lead-group, effect: reads, facts: [Name]}, {entity: campaign, effect: reads, facts: [Steps]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product starts the lead's outreach at the campaign's first step, due now
  kind: product
  entities: [{entity: lead-outreach, effect: creates, to: Queued, facts: [Current step, Next action at]}, {entity: lead, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Start outreach for a new lead

## Trigger

An agent saved a new lead, or the User imported one.

## Outcome

The lead's first invitation is planned.
