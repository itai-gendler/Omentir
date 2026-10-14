---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens Messages and picks a tab
  kind: actor
  actor: user
  entities: [{entity: conversation, effect: reads, facts: [Category]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The User opens a chat to read its full history and AI's reading of the lead's reply
  kind: actor
  actor: user
  entities: [{entity: linkedin-chat, effect: reads, facts: [Participant, Messages, Unread]}, {entity: conversation, effect: reads, facts: [Messages, Reply intent, Intent reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Read the inbox

## Trigger

The User checks on replies.

## Outcome

The User sees every conversation and what each lead's last reply meant.
