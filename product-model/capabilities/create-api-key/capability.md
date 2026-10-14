---
domain: api
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#createAgentApiKeyActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgentApiKey
- kind: code
  role: implementation
  target: src/app/(app)/api-keys/api-keys-view.tsx
---

# Create API key

The User creates an API key for an AI app, coding agent or script. The full key is shown once, when it is created.
