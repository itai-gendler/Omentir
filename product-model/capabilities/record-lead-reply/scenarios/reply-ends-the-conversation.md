---
kind: edge
routes:
  events: LinkedIn events
steps:
- text: The LinkedIn connection service delivers a lead's new message
  kind: actor
  actor: linkedin-provider
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product stores the reply and readies an AI answer
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead, effect: changes, from: Messaged, to: Replied, facts: []}, {entity: lead-outreach, effect: changes, from: Message sent, to: Reply received, facts: [Next action at]}]
  contexts:
    events: {place: linkedin-events}
- text: AI reads the reply as negative, not now or out of office
  kind: condition
  entities: [{entity: conversation, effect: reads, facts: [Reply intent]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product cancels the AI answer and stops the lead's outreach
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Reply intent, Intent reason]}, {entity: lead-outreach, effect: changes, from: Reply received, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# Reply ends the conversation

## Trigger

A lead declines or is away.

## Outcome

Nothing more is sent; a negative reply shows as Denied, the others as Needs a follow up.
