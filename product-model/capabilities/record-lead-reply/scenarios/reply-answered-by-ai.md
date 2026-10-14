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
- text: The Product stores the reply in the lead's conversation, marks the lead replied and readies an AI answer in two to fifteen minutes
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead, effect: changes, from: Messaged, to: Replied, facts: []}, {entity: lead-outreach, effect: changes, from: Message sent, to: Reply received, facts: [Next action at]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product asks the AI model to read the reply's intent and keeps it with the conversation
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Reply intent, Intent reason]}]
  contexts:
    events: {place: linkedin-events}
---

# Reply answered by AI

## Trigger

A lead in an AI-handled campaign replies.

## Outcome

AI will answer the lead shortly.
