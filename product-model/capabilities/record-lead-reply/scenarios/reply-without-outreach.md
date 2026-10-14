---
kind: edge
routes:
  events: LinkedIn events
steps:
- text: The LinkedIn connection service delivers a message from a lead with no outreach running
  kind: actor
  actor: linkedin-provider
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product stores the reply, reads its intent and emails it to the User
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages, Reply intent, Intent reason]}, {entity: workspace, effect: reads, facts: [Notification email]}, {entity: user, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# Reply without outreach

## Trigger

A lead writes on their own.

## Outcome

The User hears about the reply.
