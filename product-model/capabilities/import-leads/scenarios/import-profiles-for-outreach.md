---
kind: primary
routes:
  agent: Agent API
steps:
- text: The Connected AI app sends a CSV of LinkedIn profiles for an Outreach only agent
  kind: actor
  actor: ai-agent
  entities: [{entity: agent, effect: reads, facts: [Type]}]
  contexts:
    agent: {place: agent-api}
- text: The Product adds each profile as a lead with a fit score of 100; a person another agent already found keeps that agent as source
  kind: product
  actor: ai-agent
  entities: [{entity: lead, effect: creates, to: New, facts: [Name, LinkedIn profile, Headline, Company, Fit score, Score reasons, Summary, Lead reason, Source agent]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
---

# Import profiles for outreach

## Trigger

The User hands their AI app a list of people.

## Outcome

The imported people join the agent's campaign.
