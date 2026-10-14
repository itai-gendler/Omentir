---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits the company profile on the Workspace page and saves
  kind: actor
  actor: user
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
- text: The Product saves the company profile and refreshes the workspace's name and icon from it
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Website, Company name, Description, Pain points, Pricing details, Selling points, Buyer profile, Deal size, Name, Icon]}]
  contexts:
    web: {place: 'web-app::app::workspace-profile'}
---

# Save the company profile

## Trigger

The User wants outreach to describe the company differently.

## Outcome

Later discovery and AI messages use the edited profile.
