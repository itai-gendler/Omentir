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
- text: The campaign continues until booked, the lead shows interest or asks about pricing, and the booking link was not shared yet
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: [When a lead replies, Booking link]}, {entity: conversation, effect: reads, facts: [Reply intent]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product sends an answer that includes the booking link
  kind: product
  entities: [{entity: conversation, effect: changes, facts: [Messages]}, {entity: lead-outreach, effect: changes, from: Reply received, to: Replied, facts: []}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Share the booking link

## Trigger

An interested lead in an until-booked campaign.

## Outcome

The lead has the link to book; AI keeps the conversation until they confirm.
