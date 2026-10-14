---
kind: edge
routes:
  events: LinkedIn events
steps:
- text: The LinkedIn connection service delivers a message the User sent to a lead from LinkedIn itself
  kind: actor
  actor: linkedin-provider
  entities: [{entity: lead, effect: reads, facts: [LinkedIn profile]}, {entity: user, effect: reads, facts: []}]
  contexts:
    events: {place: linkedin-events}
- text: The Product stops all automated outreach to that lead
  kind: product
  entities: [{entity: lead-outreach, effect: changes, from: Message sent, to: Stopped, facts: [Blocked reason]}, {entity: lead, effect: changes, from: Messaged, to: Stopped, facts: []}]
  contexts:
    events: {place: linkedin-events}
---

# User wrote from linkedin

## Trigger

The User answers a lead in the LinkedIn app.

## Outcome

Automation leaves the conversation to the User.
