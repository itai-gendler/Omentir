---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app lists leads, optionally by lead group or outreach status, and reads one lead
  kind: actor
  actor: ai-agent
  entities: [{entity: lead, effect: reads, facts: [Name, Headline, Company, Fit score, Score reasons, Engagement]}, {entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    agent: {place: agent-api}
---

# List leads through the agent api

## Trigger

The User asks their AI app who was found.

## Outcome

The AI app has the leads and their context.
