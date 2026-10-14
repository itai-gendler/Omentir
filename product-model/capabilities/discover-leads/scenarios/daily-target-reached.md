---
kind: edge
routes:
  web: Web app
steps:
- text: An active agent's run time has come
  kind: condition
  unattended: true
  entities: [{entity: agent, effect: reads, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product marks the agent running
  kind: product
  entities: [{entity: agent, effect: changes, from: Active, to: Running, facts: [Last run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The agent already saved 75 leads today, or the workspace used all of today's searches
  kind: condition
  entities: [{entity: lead, effect: reads, facts: [Source agent]}, {entity: workspace, effect: reads, facts: []}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product ends the run and schedules the next one for tomorrow
  kind: product
  entities: [{entity: agent, effect: changes, from: Running, to: Active, facts: [Next run]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Daily target reached

## Trigger

A busy day for the workspace.

## Outcome

No more leads are looked for today; the counts reset at local midnight.
