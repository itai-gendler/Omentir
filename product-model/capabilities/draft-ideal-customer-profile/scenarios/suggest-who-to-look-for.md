---
kind: primary
routes:
  web: Web app
steps:
- text: The User asks AI to suggest who the agent should look for
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product asks the AI model to draft a prospect description, job titles, industries, locations and keywords from the company profile and fills them in, unsaved
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Description, Pain points, Buyer profile]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Suggest who to look for

## Trigger

The User starts a new agent.

## Outcome

The setup holds AI's suggestions, which the User can change.
