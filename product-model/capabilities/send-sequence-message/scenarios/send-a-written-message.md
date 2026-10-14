---
kind: primary
routes:
  web: Web app
steps:
- text: A connected lead's outreach is due on a message step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Current step]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: It is inside the send window, today's message limit is not used up and the account's last action was more than five minutes ago
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: [Send window]}, {entity: workspace, effect: reads, facts: [Daily message limit]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product sends the message the User wrote for this lead, or the campaign's written message with the lead's details filled in
  kind: product
  entities: [{entity: lead-outreach, effect: reads, facts: [Your messages]}, {entity: campaign, effect: reads, facts: [Steps]}, {entity: lead, effect: reads, facts: [Name, Company]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product records the message in the lead's conversation, marks the lead messaged and moves on to the next step
  kind: product
  entities: [{entity: conversation, effect: creates, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Connected, to: Message sent, facts: [Current step, Next action at]}, {entity: lead, effect: changes, from: Connected, to: Messaged, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Send a written message

## Trigger

The campaign's wait after the acceptance is over.

## Outcome

The message is sent and recorded; the next step follows the campaign's wait.
