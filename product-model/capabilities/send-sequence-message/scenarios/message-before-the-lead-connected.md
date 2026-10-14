---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's outreach is due on a message step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead has not accepted an invitation
  kind: condition
  entities: [{entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product holds the message and marks the outreach as an error until the lead connects
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Error, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Message before the lead connected

## Trigger

A campaign's first step is a message to someone who is not a connection.

## Outcome

The message waits; it is checked again daily.
