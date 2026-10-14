---
kind: primary
routes:
  web: Web app
steps:
- text: A connected lead's outreach is due on an AI message step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Current step]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product sends the message AI drafted during the wait, or asks the AI model now using the lead's profile, the company profile, the campaign's goal and tone and the conversation so far
  kind: product
  entities: [{entity: lead-outreach, effect: reads, facts: [Prepared message]}, {entity: lead, effect: reads, facts: [Summary, Headline, Company]}, {entity: workspace, effect: reads, facts: [Description, Pain points, Selling points]}, {entity: campaign, effect: reads, facts: [Goal, Message tone]}, {entity: conversation, effect: reads, facts: [Messages]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product records the message, marks the lead messaged and moves on
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Connected, to: Message sent, facts: [Current step, Next action at]}, {entity: lead, effect: changes, from: Connected, to: Messaged, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Send an ai message

## Trigger

An AI-written step is due.

## Outcome

The message the User could review in advance is the one that was sent.
