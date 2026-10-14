---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens an agent's actions
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
- text: The Product lists each upcoming invitation and message with its lead, its time and the message that will be sent, or why it is blocked
  kind: product
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Prepared message, Your messages, Blocked reason]}, {entity: lead, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
- text: The User reads one lead's next action and the conversation so far
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Prepared message]}, {entity: conversation, effect: reads, facts: [Messages]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
---

# Read an agents upcoming actions

## Trigger

The User wants to know what will be sent in their name.

## Outcome

The User sees every upcoming action and its message.
