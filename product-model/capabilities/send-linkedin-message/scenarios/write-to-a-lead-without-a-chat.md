---
kind: primary
routes:
  web: Web app
steps:
- text: The User writes to a lead whose chat is not in the inbox yet
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product sends the message to the lead directly, records it and stops the lead's automated outreach
  kind: product
  actor: user
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Message sent, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Write to a lead without a chat

## Trigger

The User follows up on a lead from their conversation.

## Outcome

The message is sent; LinkedIn uses the existing chat.
