---
kind: primary
routes:
  web: Web app
steps:
- text: Five minutes have passed since an account's recent messages were last checked
  kind: condition
  unattended: true
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product stores replies the events missed and handles each like a delivered reply
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead, effect: changes, from: Messaged, to: Replied, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Reply found by the check

## Trigger

An event was lost.

## Outcome

No reply goes unnoticed for long.
