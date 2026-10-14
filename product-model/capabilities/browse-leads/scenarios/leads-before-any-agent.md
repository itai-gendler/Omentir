---
kind: edge
routes:
  web: Web app
steps:
- text: The User opens Leads
  kind: actor
  actor: user
  entities: [{entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The workspace has no agent yet
  kind: condition
  entities: [{entity: agent, effect: reads, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product asks the User to start an agent on Overview first
  kind: product
  entities: [{entity: user, effect: reads, facts: []}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Leads before any agent

## Trigger

A new workspace.

## Outcome

The User is pointed at setting up an agent.
