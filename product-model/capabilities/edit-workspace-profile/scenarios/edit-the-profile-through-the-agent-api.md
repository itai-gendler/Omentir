---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app sends changes to the company profile
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent: {place: agent-api}
- text: The Product saves the changed fields and keeps the rest
  kind: product
  actor: ai-agent
  entities: [{entity: workspace, effect: changes, facts: [Company name, Description, Pain points, Pricing details, Demo booking link, Selling points, Buyer profile]}]
  contexts:
    agent: {place: agent-api}
---

# Edit the profile through the agent api

## Trigger

The User asks their AI app to adjust the company profile.

## Outcome

The company profile holds the changes.
