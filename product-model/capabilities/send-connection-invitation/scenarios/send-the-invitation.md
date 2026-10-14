---
kind: primary
routes:
  web: Web app
steps:
- text: A lead's outreach is due on an invitation step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at, Current step]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: It is inside the send window on the lead's clock, today's invite limit is not used up and the account's last action was more than five minutes ago
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: [Send window]}, {entity: lead, effect: reads, facts: [Location]}, {entity: workspace, effect: reads, facts: [Daily invite limit, Time zone]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product sends the invitation from the campaign's sending account, with a note only when the User wrote one
  kind: product
  entities: [{entity: campaign, effect: reads, facts: [Steps, Sending account]}, {entity: lead-outreach, effect: changes, from: Queued, to: Invitation sent, facts: [Current step, Invitation sent at, Next action at]}, {entity: lead, effect: changes, from: New, to: Invited, facts: []}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Send the invitation

## Trigger

The lead's invitation is due.

## Outcome

The invitation is out; the next step waits for the lead to accept.
