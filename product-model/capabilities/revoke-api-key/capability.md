---
domain: api
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#revokeAgentApiKeyActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#revokeAgentApiKey
---

# Revoke API key

The User revokes an API key so no AI app can use it again.
