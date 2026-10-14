---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks for a lead group's CSV
  kind: actor
  actor: ai-agent
  entities: [{entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
- text: The Product returns the CSV
  kind: product
  entities: [{entity: lead, effect: reads, facts: [Name, Headline, Company, LinkedIn profile, Fit score]}]
  contexts:
    agent: {place: agent-api}
---

# Export through the agent api

## Trigger

The User asks their AI app for the list.

## Outcome

The AI app has the CSV.
