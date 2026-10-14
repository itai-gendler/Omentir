---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Sign out in Settings
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
- text: The Product ends the session
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::settings'}
---

# Sign out from settings

## Trigger

The User is done on this device.

## Outcome

The User is signed out and sent to the sign-in page.
