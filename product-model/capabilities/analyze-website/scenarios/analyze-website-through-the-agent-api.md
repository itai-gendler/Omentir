---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks Omentir to read a website
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent: {place: agent-api}
- text: The Product fills the company profile from the site
  kind: product
  actor: ai-agent
  entities: [{entity: workspace, effect: changes, facts: [Website, Company name, Description, Pain points, Pricing details, Selling points, Buyer profile]}]
  contexts:
    agent: {place: agent-api}
---

# Analyze website through the agent api

## Trigger

The User asks their AI app to set up the workspace from their site.

## Outcome

The company profile is filled from the website.
