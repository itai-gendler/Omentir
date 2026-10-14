---
kind: edge
routes:
  web: Web app
steps:
- text: A lead is in the lead group of an active campaign
  kind: condition
  unattended: true
  entities: [{entity: lead, effect: reads, facts: [Source agent]}, {entity: lead-group, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead was already contacted, was found by a leads-only agent, or its agent is paused or deleted
  kind: condition
  entities: [{entity: agent, effect: reads, facts: [Leads only]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product does not start outreach for that lead
  kind: product
  entities: [{entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Lead not eligible for outreach

## Trigger

A lead that must not be contacted sits in a campaign's group.

## Outcome

Nothing is planned for the lead.
