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
- text: AI reads hot interest and the campaign continues until interest
  kind: condition
  entities: [{entity: conversation, effect: reads, facts: [Reply intent]}, {entity: campaign, effect: reads, facts: [When a lead replies]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product cancels the AI answer and emails the User the interested lead's profile and reply, once
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Reply intent, Intent reason]}, {entity: lead-outreach, effect: changes, from: Reply received, to: Stopped, facts: [Blocked reason]}, {entity: workspace, effect: reads, facts: [Notification email]}, {entity: user, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# Interest detected

## Trigger

A lead asks for a call.

## Outcome

The User takes over a hot lead.
