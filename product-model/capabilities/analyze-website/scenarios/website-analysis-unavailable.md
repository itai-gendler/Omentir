---
kind: edge
routes:
  profile: Workspace page
steps:
- text: The User asks Omentir to read the company website again
  kind: actor
  actor: user
  entities: []
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
- text: The AI model cannot read or summarise the site
  kind: condition
  entities: []
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
- text: The Product keeps the previous company profile and says the analysis did not work
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description]}]
  contexts:
    profile: {place: 'web-app::app::workspace-profile'}
---

# Website analysis unavailable

## Trigger

The model or the site is unavailable during a re-analysis.

## Outcome

Nothing in the company profile changes.
