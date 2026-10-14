---
kind: edge
routes:
  web: Web app
steps:
- text: A lead's outreach is due on an invitation step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: LinkedIn refused invitations from the account to three different people in a row
  kind: condition
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product pauses invitations on that account, tries a single invitation later, parks the rest until the pause ends, and emails the User once that day
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Notification email]}, {entity: lead-outreach, effect: changes, facts: [Next action at]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Linkedin pauses invitations

## Trigger

LinkedIn limits the account's invitations.

## Outcome

Invitations resume when the pause ends, or earlier if the trial invitation goes through.

## Edge cases

- When LinkedIn refuses one person because an earlier invitation to them is still pending, only that lead waits three weeks.
