---
kind: edge
routes:
  web: Web app
steps:
- text: The User chooses Delete workspace on their first workspace and confirms
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
- text: The Product pauses the workspace's agents
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, from: Active, to: Paused, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
- text: The Product deletes the agents, lead groups and campaigns and resets the workspace's name, keeping it empty with the User's account and billing
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: removes}, {entity: agent, effect: removes, from: Paused, with: lead-group}, {entity: campaign, effect: removes, with: lead-group}, {entity: workspace, effect: changes, facts: [Name, Icon]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
---

# Empty the first workspace

## Trigger

The User deletes the workspace they signed up with.

## Outcome

An empty workspace remains; the subscription is untouched.
