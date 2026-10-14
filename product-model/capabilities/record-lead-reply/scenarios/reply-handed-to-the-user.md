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
- text: The campaign stops after the first reply
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: [When a lead replies, Email me when a lead replies]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product stores the reply, ends the sequence and emails the reply to the User unless they turned that off
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead, effect: changes, from: Messaged, to: Replied, facts: []}, {entity: lead-outreach, effect: changes, from: Message sent, to: Replied, facts: []}, {entity: workspace, effect: reads, facts: [Notification email]}, {entity: user, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# Reply handed to the user

## Trigger

A lead in a hand-off campaign replies.

## Outcome

The User owns the conversation from here.
