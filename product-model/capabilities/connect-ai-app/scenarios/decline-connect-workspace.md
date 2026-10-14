---
kind: validation
routes:
  web: Web app
steps:
- text: The User declines the AI app's request
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web-app::app::connect-ai-app'}
- text: The Product tells the AI app access was denied
  kind: product
  entities: []
  contexts:
    web: {place: 'web-app::app::connect-ai-app'}
---

# Decline connect workspace

## Trigger

The User does not recognise the request.

## Outcome

No key is issued.
