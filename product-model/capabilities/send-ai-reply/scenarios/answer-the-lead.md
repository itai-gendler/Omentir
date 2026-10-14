---
kind: primary
routes:
  web: Web app
steps:
- text: A lead's AI answer is due
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The account's last action was more than five minutes ago
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product asks the AI model for an answer using the conversation, the reply's intent, the company profile and the campaign's goal and tone
  kind: product
  entities: [{entity: conversation, effect: reads, facts: [Messages, Reply intent, Intent reason]}, {entity: workspace, effect: reads, facts: [Description, Pricing details, Selling points]}, {entity: campaign, effect: reads, facts: [Goal, Message tone]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product sends the answer, records it and waits for the lead's next message
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Reply received, to: Replied, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Answer the lead

## Trigger

A lead's reply was stored a few minutes ago.

## Outcome

The lead has an answer; the next reply is handled the same way.
