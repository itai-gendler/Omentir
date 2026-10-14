---
kind: primary
routes:
  profile: Workspace page
  onboarding: Onboarding
steps:
- text: The User enters the company website and asks Omentir to read it
  kind: actor
  actor: user
  entities: []
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
    onboarding: {place: 'web-app::app::onboarding'}
- text: The Product asks the AI model to read the site and fills the company profile
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Website, Company name, Description, Pain points, Pricing details, Selling points, Buyer profile]}]
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
    onboarding: {place: 'web-app::app::onboarding'}
- text: The Product takes the workspace's name and icon from the site
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Name, Icon]}]
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
    onboarding: {place: 'web-app::app::onboarding'}
---

# Fill the profile from the website

## Trigger

The User wants Omentir to understand what they sell without typing it all.

## Outcome

The company profile is filled from the website; the demo booking link, the LinkedIn company page and the deal size keep their earlier values.
