---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits the company information shown while setting up an agent
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product saves the company name, industry and size, description, pain points and website
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Company name, Description, Pain points, Website]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Edit company information during agent setup

## Trigger

The User notices the company information is off while creating an agent.

## Outcome

The agent setup continues with the corrected company information.
