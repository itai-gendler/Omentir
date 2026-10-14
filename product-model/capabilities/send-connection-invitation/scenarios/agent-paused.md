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
- text: The agent that found the lead is paused
  kind: condition
  entities: [{entity: agent, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product parks the invitation until the agent is resumed
  kind: product
  entities: [{entity: lead-outreach, effect: changes, facts: [Next action at]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Agent paused

## Trigger

The User paused the agent.

## Outcome

Nothing is sent to the lead while the agent is paused.
