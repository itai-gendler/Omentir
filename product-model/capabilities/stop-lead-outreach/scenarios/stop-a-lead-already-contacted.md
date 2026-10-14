---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Stop outreach for a lead who was already messaged and confirms
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
- text: The Product stops the lead's outreach and keeps the lead's stage
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, from: Message sent, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
---

# Stop a lead already contacted

## Trigger

The User takes a lead out of the sequence.

## Outcome

No further message or AI reply goes out.
