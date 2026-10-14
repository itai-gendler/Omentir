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
- text: Today's invite limit is used up
  kind: condition
  entities: [{entity: workspace, effect: reads, facts: [Daily invite limit, Time zone]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product moves the invitation to the next local day with room
  kind: product
  entities: [{entity: lead-outreach, effect: changes, facts: [Next action at]}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Daily invite limit used up

## Trigger

The workspace already sent its invitations for today.

## Outcome

The invitation goes out on a later day.
