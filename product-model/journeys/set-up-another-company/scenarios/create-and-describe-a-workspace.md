---
kind: primary
result: achieved
routes:
  web: Web app
steps:
- text: The User creates a new workspace from its landing page
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app'}
  capability: create-workspace
- text: The Product creates the workspace and opens its company profile
  kind: product
  actor: user
  entities: [{entity: workspace, effect: creates, facts: [Name, Icon, Website, Time zone, Notification email, Daily invite limit, Daily message limit, First message delay, Daily summary, Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
  capability: create-workspace
- text: The User fills in the company profile and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
  capability: edit-workspace-profile
- text: The Product saves the company profile
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Company name, Description, Pain points, Buyer profile]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
  capability: edit-workspace-profile
---

# Create and describe a workspace

## Trigger

The User sells for a second company.

## Outcome

The new workspace is ready for agents.
