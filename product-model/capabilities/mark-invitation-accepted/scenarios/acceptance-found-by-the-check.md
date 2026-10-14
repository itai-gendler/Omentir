---
kind: primary
routes:
  web: Web app
steps:
- text: Two hours have passed since the account's invitations were last checked
  kind: condition
  unattended: true
  entities: [{entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product compares the account's pending invitations with its connections and marks the leads who accepted
  kind: product
  entities: [{entity: lead, effect: changes, from: Invited, to: Connected, facts: []}, {entity: lead-outreach, effect: changes, from: Invitation sent, to: Connected, facts: [Current step, Next action at]}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Acceptance found by the check

## Trigger

The acceptance event did not arrive.

## Outcome

Accepted leads move on to messaging within hours.
