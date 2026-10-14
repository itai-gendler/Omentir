---
kind: primary
routes:
  web: Web app
steps:
- text: The User pastes a meeting scheduler link in the Overview checklist
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::overview'}
- text: The Product saves the demo booking link and copies it onto every campaign that continues until booked and has no link of its own
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Demo booking link]}, {entity: campaign, effect: changes, facts: [Booking link]}]
  contexts:
    web: {place: 'web-app::app::overview'}
---

# Add a booking link from overview

## Trigger

The User completes the booking-link setup step.

## Outcome

The workspace has a demo booking link; campaigns with their own link keep it.
