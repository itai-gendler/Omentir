---
kind: edge
routes:
  web: Web app
steps:
- text: The User launches an agent with outreach
  kind: actor
  actor: user
  entities: [{entity: agent, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the agent
  kind: product
  actor: user
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Prospect description, Job titles, Industries, Locations, Keywords, Sending account, Leads only, Daily run time, Next run]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: Creating the campaign fails
  kind: condition
  entities: [{entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product deletes the new agent again and shows the error
  kind: product
  actor: user
  entities: [{entity: agent, effect: removes, from: Active}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
---

# Launch fails after the agent was created

## Trigger

Something fails at the last step of the launch.

## Outcome

No half-made agent is left counting against the plan.
