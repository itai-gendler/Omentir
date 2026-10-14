---
kind: primary
routes:
  web: Web app
steps:
- text: The User switches a paused agent back on
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
- text: The Product makes the agent active and due now, and wakes the outreach that waited for it
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, from: Paused, to: Active, facts: [Next run]}, {entity: lead-outreach, effect: changes, facts: [Next action at]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Switch an agent back on

## Trigger

The User wants the agent working again.

## Outcome

The agent looks for leads within minutes and its leads' outreach resumes.
