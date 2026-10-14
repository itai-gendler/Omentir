---
kind: edge
routes:
  web: Web app
steps:
- text: A connected lead's outreach is due on a message step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead's LinkedIn chat has a message the User sent outside the sequence
  kind: condition
  entities: [{entity: linkedin-chat, effect: reads, facts: [Messages]}, {entity: user, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product stops the lead's outreach instead of sending
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Connected, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: changes, from: Connected, to: Stopped, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# User already messaged the lead

## Trigger

The User wrote to the lead directly on LinkedIn.

## Outcome

Automation leaves the conversation to the User.
