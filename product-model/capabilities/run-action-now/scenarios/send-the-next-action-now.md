---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Send now on a lead's next invitation and confirms
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product sends the invitation right away
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Invitation sent, facts: [Current step, Invitation sent at, Next action at]}, {entity: lead, effect: changes, from: New, to: Invited, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Send the next action now

## Trigger

The User does not want to wait for the schedule.

## Outcome

The invitation is out now.
