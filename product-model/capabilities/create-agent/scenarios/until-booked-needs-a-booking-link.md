---
kind: validation
routes:
  web: Web app
steps:
- text: The User picks Continue until booked with no booking link
  kind: actor
  actor: user
  entities: [{entity: campaign, effect: reads, facts: [When a lead replies, Booking link]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The workspace has no demo booking link either
  kind: condition
  entities: [{entity: workspace, effect: reads, facts: [Demo booking link]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product refuses and asks for a booking link here or in Workspace
  kind: product
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Until booked needs a booking link

## Trigger

The User wants AI to book meetings without a link to share.

## Outcome

Nothing is created.
