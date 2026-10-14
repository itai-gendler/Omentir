---
kind: primary
routes:
  web: Web app
steps:
- text: The User marks a conversation's follow-up done
  kind: actor
  actor: user
  entities: [{entity: conversation, effect: reads, facts: [Category]}]
  contexts:
    web: {place: 'web-app::app::messages'}
- text: The Product records when the follow-up was done
  kind: product
  actor: user
  entities: [{entity: conversation, effect: changes, facts: [Follow-up done at]}]
  contexts:
    web: {place: 'web-app::app::messages'}
---

# Mark done

## Trigger

The User followed up with a lead.

## Outcome

The conversation is no longer under Needs a follow up.
