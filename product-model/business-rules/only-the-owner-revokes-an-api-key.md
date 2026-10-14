---
appliesTo:
- type: entity
  id: api-key
  effect: changes
  to: Revoked
permits:
- related:
  - {verb: issues, entity: workspace}
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#revokeAgentApiKey
---

# Only the workspace's owner revokes its API keys

Revoking needs no active subscription.
