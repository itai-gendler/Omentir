---
kind: edge
routes:
  web: Web app
steps:
- text: The daily summary hour passed while Omentir was not running
  kind: condition
  unattended: true
  entities: [{entity: workspace, effect: reads, facts: [Daily summary hour]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product still sends the summary within two hours of the chosen hour, and otherwise skips that day
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Notification email]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Summary hour missed

## Trigger

An outage around the chosen hour.

## Outcome

A late summary arrives the same morning or not at all.
