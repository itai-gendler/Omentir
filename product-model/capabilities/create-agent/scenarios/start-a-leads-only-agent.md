---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Only Lead, describes the prospects with job titles, industries, locations and keywords, names the group and picks the sending LinkedIn account
  kind: actor
  actor: user
  entities: [{entity: linkedin-account, effect: reads, facts: [Display name]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the lead group, or uses the existing group of that name
  kind: product
  actor: user
  entities: [{entity: lead-group, effect: creates, facts: [Name, Lead count]}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product creates the agent as leads only, active and due to look for leads now
  kind: product
  actor: user
  entities: [{entity: agent, effect: creates, to: Active, facts: [Name, Type, Prospect description, Job titles, Industries, Locations, Keywords, Sending account, Leads only, Daily run time, Next run]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::agent-setup'}
- text: The Product opens AI Agents
  kind: product
  entities: [{entity: agent, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web-app::app::agents'}
---

# Start a leads only agent

## Trigger

The User wants a list of matching people to contact themselves.

## Outcome

The agent finds leads from the next automation run; nobody it finds is contacted automatically.
