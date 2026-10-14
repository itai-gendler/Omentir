---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's outreach is due on an invitation step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead is already a first-degree connection of the sending account
  kind: condition
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product skips the invitation and moves on to messaging
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Connected, facts: [Current step]}, {entity: lead, effect: changes, from: New, to: Connected, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Lead already connected

## Trigger

The User already knows the lead.

## Outcome

The sequence continues with its first message.
