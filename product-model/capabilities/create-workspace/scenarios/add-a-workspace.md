---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses New workspace and enters the landing page and, optionally, a name
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app'}
- text: The Product creates the workspace with the first workspace's time zone, notification email and sending limits, takes its icon from the site and makes it the active one
  kind: product
  actor: user
  entities: [{entity: workspace, effect: creates, facts: [Name, Icon, Website, Time zone, Notification email, Daily invite limit, Daily message limit, First message delay, Daily summary, Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app'}
- text: The Product opens the new workspace's company profile
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Website]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
---

# Add a workspace

## Trigger

The User sells for a second company.

## Outcome

The User is on the new workspace's Workspace page, with its daily summary off.
