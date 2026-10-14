---
kind: primary
routes:
  web: Web app
steps:
- text: The User rewrites the lead's next message and saves
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Prepared message]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product keeps the message for this lead and step
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, facts: [Your messages]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Rewrite the next message

## Trigger

The User wants to personalise a message.

## Outcome

That exact text is what will be sent.
