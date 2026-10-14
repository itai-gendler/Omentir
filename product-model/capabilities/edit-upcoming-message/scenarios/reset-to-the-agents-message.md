---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Reset to agent message
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Your messages]}, {entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
- text: The Product forgets the User's text; the campaign's message or AI's draft goes out instead
  kind: product
  actor: user
  entities: [{entity: lead-outreach, effect: changes, facts: [Your messages]}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-actions'}
---

# Reset to the agents message

## Trigger

The User changes their mind.

## Outcome

The agent's message is back.
