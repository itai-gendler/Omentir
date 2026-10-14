---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Delete workspace on a workspace they added and confirms
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product pauses the workspace's agents so nothing more is sent
  kind: product
  actor: user
  entities: [{entity: agent, effect: changes, from: Active, to: Paused, facts: []}, {entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product keeps its LinkedIn accounts on the User's other workspaces and deletes the workspace with its agents, lead groups and campaigns
  kind: product
  actor: user
  entities: [{entity: workspace, effect: removes}, {entity: agent, effect: removes, from: Paused, with: workspace}, {entity: lead-group, effect: removes, with: workspace}, {entity: campaign, effect: removes, with: lead-group}, {entity: linkedin-account, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Delete an added workspace

## Trigger

The User no longer sells for that company.

## Outcome

The workspace is gone from the switcher; LinkedIn stays connected for the User's other workspaces.
