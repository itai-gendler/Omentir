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
- text: It is outside the campaign's send window on the lead's clock
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: [Send window]}, {entity: lead, effect: reads, facts: [Location]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product moves the invitation to the next opening of the window
  kind: product
  entities: [{entity: lead-outreach, effect: changes, facts: [Next action at]}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Outside the send window

## Trigger

A business-hours campaign comes due at night for the lead.

## Outcome

The invitation goes out when the lead's working day starts.
