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
- text: The self-hosted install's live sending is not enabled
  kind: condition
  entities: []
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product records what it would send and sends nothing
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Dry run on a self hosted install

## Trigger

The operator has not enabled live sending yet.

## Outcome

Nothing reaches LinkedIn; the decisions can be reviewed.
