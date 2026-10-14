---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's invitation has been pending for 21 days
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Invitation sent at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: A last check finds the lead has not accepted
  kind: condition
  entities: [{entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product stops the lead's outreach
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Invitation sent, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Invitation never accepted

## Trigger

The lead ignores the invitation.

## Outcome

Nothing more is sent to the lead.
