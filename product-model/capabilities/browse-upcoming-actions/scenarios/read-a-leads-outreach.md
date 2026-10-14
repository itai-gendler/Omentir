---
kind: primary
routes:
  web: Web app
steps:
- text: The User selects a lead on Leads
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: [Name, Fit score]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The User reads the lead's outreach steps, done and to come, and the next action
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Current step, Next action at, Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Read a leads outreach

## Trigger

The User looks into one lead.

## Outcome

The User knows where the lead is in the sequence.
