---
kind: validation
routes:
  web: Web app
steps:
- text: The User chooses Send now on a lead's next action
  kind: actor
  actor: user
  entities: [{entity: lead-outreach, effect: reads, facts: [Next action at]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The lead's outreach was stopped, its agent is paused, deleted or leads only, or the campaign is not active
  kind: condition
  entities: [{entity: agent, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product refuses and says why
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Send now refused

## Trigger

The action may not run.

## Outcome

Nothing is sent.

## Edge cases

- A message to a lead who has not accepted is refused after one live check, unless that check finds they accepted.
- A self-hosted install without live sending refuses every Send now.
