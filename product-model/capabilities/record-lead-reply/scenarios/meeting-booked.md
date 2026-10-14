---
kind: primary
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
- text: AI reads a confirmed meeting
  kind: condition
  entities: [{entity: conversation, effect: reads, facts: [Reply intent]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product records the meeting, cancels the AI answer and emails the User, once
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Reply intent, Meeting booked at]}, {entity: lead-outreach, effect: changes, from: Reply received, to: Stopped, facts: [Blocked reason]}, {entity: workspace, effect: reads, facts: [Notification email]}, {entity: user, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# Meeting booked

## Trigger

A lead confirms they booked.

## Outcome

The meeting counts on Overview and the conversation is Successful.
