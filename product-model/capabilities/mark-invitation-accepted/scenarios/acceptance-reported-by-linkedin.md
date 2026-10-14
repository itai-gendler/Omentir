---
kind: primary
routes:
  events: LinkedIn events
steps:
- text: The LinkedIn connection service reports that a lead accepted the invitation
  kind: actor
  actor: linkedin-provider
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}]
  contexts:
    events: {place: linkedin-events}
- text: The Product marks the lead connected, moves the outreach to its next step and prepares the next message
  kind: product
  entities: [{entity: lead, effect: changes, from: Invited, to: Connected, facts: []}, {entity: lead-outreach, effect: changes, from: Invitation sent, to: Connected, facts: [Current step, Next action at, Prepared message]}]
  contexts:
    events: {place: linkedin-events}
---

# Acceptance reported by linkedin

## Trigger

The lead accepts on LinkedIn.

## Outcome

The first message is planned after the campaign's wait.
