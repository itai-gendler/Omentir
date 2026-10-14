---
kind: primary
routes:
  web: Web app
steps:
- text: The workspace's daily summary hour has come and the summary is on
  kind: condition
  unattended: true
  entities: [{entity: workspace, effect: reads, facts: [Daily summary, Daily summary hour, Time zone]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The User has an active subscription
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Subscription status]}]
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product emails the last 24 hours of new leads, invitations, accepted connections, messages and replies to the notification email
  kind: product
  entities: [{entity: workspace, effect: reads, facts: [Notification email]}, {entity: lead, effect: reads, facts: []}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Email the daily summary

## Trigger

The chosen hour.

## Outcome

The User has the day's summary in their inbox, once.
