---
kind: primary
routes:
  events: LinkedIn events
steps:
- text: AI already answered the lead and the last intent did not end the conversation
  kind: condition
  entities: [{entity: lead-outreach, effect: reads, facts: []}, {entity: conversation, effect: reads, facts: [Reply intent]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
- text: The LinkedIn connection service delivers the lead's next message
  kind: actor
  actor: linkedin-provider
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product stores it and readies another AI answer
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Replied, to: Reply received, facts: [Next action at]}]
  contexts:
    events: {place: linkedin-events}
---

# Lead writes again

## Trigger

A multi-turn conversation continues.

## Outcome

AI keeps the conversation until its stopping point.
