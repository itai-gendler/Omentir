---
appliesTo:
- type: entity
  id: api-key
  effect: creates
permits:
- related:
  - {verb: issues, entity: workspace}
  - {verb: owns, entity: user}
  when:
  - {entity: user, fact: Subscription status, is: Active}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgentApiKey
- kind: code
  role: implementation
  target: src/lib/plan-limits.ts#planHasApiAccess
---

# Only the workspace's owner creates an API key, and only with an active subscription

Every paid plan includes the agent API; without an active subscription no key is created or issued to an AI app.
