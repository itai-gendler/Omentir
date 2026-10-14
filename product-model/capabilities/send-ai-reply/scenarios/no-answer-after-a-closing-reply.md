---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's AI answer is due
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The reply was negative, not now, out of office or a confirmed meeting, or the campaign now stops after the first reply
  kind: condition
  entities: [{entity: conversation, effect: reads, facts: [Reply intent]}, {entity: campaign, effect: reads, facts: [When a lead replies]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product sends nothing and stops the lead's outreach
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Reply received, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# No answer after a closing reply

## Trigger

The conversation reached its end before the answer went out.

## Outcome

Nothing is sent.
