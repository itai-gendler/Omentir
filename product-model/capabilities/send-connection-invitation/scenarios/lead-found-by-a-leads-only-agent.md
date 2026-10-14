---
kind: validation
routes:
  web: Web app
steps:
- text: A lead's outreach is due on an invitation step
  kind: condition
  unattended: true
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead was found by a leads-only agent
  kind: condition
  entities: [{entity: lead, effect: reads, facts: [Source agent]}, {entity: agent, effect: reads, facts: [Leads only]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product stops the lead's outreach without sending
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Queued, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Lead found by a leads only agent

## Trigger

The lead's agent was made leads only.

## Outcome

The lead is never invited automatically.

## Edge cases

- An anonymous LinkedIn Member profile is stopped the same way, since it cannot be contacted.
