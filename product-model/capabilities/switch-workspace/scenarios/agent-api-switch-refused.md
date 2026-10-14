---
kind: validation
routes:
  agent: Agent API
steps:
- text: The Connected AI app asks to switch to a workspace
  kind: actor
  actor: ai-agent
  entities: [{entity: workspace, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The workspace is not one of the User's, or a self-hosted install has only its one workspace
  kind: condition
  entities: [{entity: workspace, effect: reads, facts: []}, {entity: user, effect: reads, facts: []}]
  contexts:
    agent: {place: agent-api}
- text: The Product refuses the switch and the key stays where it was
  kind: product
  entities: []
  contexts:
    agent: {place: agent-api}
---

# Agent api switch refused

## Trigger

An AI app asks for a workspace it cannot use.

## Outcome

Nothing changes.
