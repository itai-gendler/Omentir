---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's outreach is due on another AI message
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: AI has already sent three messages to the lead with no reply
  kind: condition
  entities: [{entity: conversation, effect: reads, facts: [Messages]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product stops the lead's outreach and records that the sequence finished
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Message sent, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Ai sequence ends unanswered

## Trigger

The lead stays silent.

## Outcome

No more messages go to the lead; nobody is emailed about the silence.
