---
kind: primary
routes:
  web: Web app
steps:
- text: The User writes a reply in a LinkedIn chat, optionally with attachments under 15 MB, and sends it
  kind: actor
  actor: user
  entities: [{entity: linkedin-chat, effect: reads, facts: [Participant]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product sends it from the LinkedIn account that owns the chat and records it in the lead's conversation
  kind: product
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}, {entity: linkedin-chat, effect: changes, facts: [Messages]}, {entity: conversation, effect: changes, facts: [Messages]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product stops the lead's automated outreach, since the User now owns the conversation
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, from: Reply received, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: changes, from: Replied, to: Stopped, facts: []}, {entity: conversation, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Reply in a chat

## Trigger

A lead's reply needs a personal answer.

## Outcome

The lead has the User's reply and no automated message follows it.
