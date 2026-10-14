---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Send now on an upcoming message in an agent's actions and confirms
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Prepared message]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
- text: The Product sends the message right away and records it
  kind: product
  actor: user
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Connected, to: Message sent, facts: [Current step, Next action at]}, {entity: lead, effect: changes, from: Connected, to: Messaged, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
---

# Send now from an agents actions

## Trigger

The User wants a follow-up out today.

## Outcome

The message is sent.
