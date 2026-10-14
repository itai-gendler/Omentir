---
appliesTo:
- type: entity
  id: agent
  effect: creates
permits:
- related:
  - {verb: runs, entity: workspace}
  - {verb: owns, entity: user}
  when:
  - &id001 {entity: user, fact: Subscription status, is: Active}
- related:
  - {verb: runs, entity: workspace}
  - {verb: owns, entity: user}
  - {verb: connects, entity: ai-agent}
  when:
  - *id001
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#createAgentForSetupActionImpl
- kind: code
  role: implementation
  target: src/lib/server/subscription.ts#requireActiveSubscription
- kind: code
  role: implementation
  target: src/lib/server/agent-api.ts#requireAgentApiContext
---

# Only the workspace's owner, or an AI app they connected, creates an agent, and only with an active subscription

Creating an agent is refused without an active subscription, in the app and through the agent API alike. A self-hosted install is always subscribed.

## Rationale

Agents spend paid LinkedIn searches and AI calls; the subscription pays for them.
