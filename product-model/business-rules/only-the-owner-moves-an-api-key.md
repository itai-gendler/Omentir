---
appliesTo:
- type: entity
  id: api-key
  effect: changes
permits:
- related:
  - {verb: issues, entity: workspace}
  - {verb: owns, entity: user}
- related:
  - {verb: issues, entity: workspace}
  - {verb: owns, entity: user}
  - {verb: connects, entity: ai-agent}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#setAgentApiKeyWorkspace
---

# Only the workspace's owner, or an AI app using the key, changes an API key

An AI app moves its key to another of the User's workspaces; only the User revokes it.
