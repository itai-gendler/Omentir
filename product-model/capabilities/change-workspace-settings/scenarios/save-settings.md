---
kind: primary
routes:
  web: Web app
steps:
- text: The User changes the time zone, limits, daily summary or invite withdrawal and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product saves the settings; dates, daily limits and the summary hour follow the new time zone
  kind: product
  actor: user
  entities: [{entity: workspace, effect: changes, facts: [Time zone, Daily invite limit, Daily message limit, First message delay, Daily summary, Daily summary hour, Invite withdrawal]}]
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Save settings

## Trigger

The User wants Omentir to send more slowly, or on their own clock.

## Outcome

Later outreach follows the new limits and time zone.
