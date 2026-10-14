---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes a lead group and confirms
  kind: actor
  actor: user
  entities: [{entity: lead-group, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: No agent or campaign uses the group
  kind: condition
  entities: [{entity: agent, effect: reads, facts: []}, {entity: campaign, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::leads'}
- text: The Product deletes the group with its leads, their outreach and conversations
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: removes}, {entity: lead, effect: removes, from: New, with: lead-group}, {entity: conversation, effect: removes, with: lead}]
  contexts:
    web: {place: 'web-app::app::leads'}
---

# Delete an unused lead group

## Trigger

The User cleans up a group they no longer need.

## Outcome

The group and its leads are gone; Overview's history keeps their counts.
