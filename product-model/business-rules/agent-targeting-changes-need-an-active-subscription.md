---
appliesTo:
- type: entity
  id: agent
  effect: changes
  facts:
  - Prospect description
  - Job titles
  - Industries
  - Locations
  - Keywords
  - Sending account
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
  target: src/app/actions.ts#updateAgentActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#updateAgentForSetupActionImpl
---

# Only the workspace's owner, or an AI app they connected, changes an agent's targeting, and only with an active subscription

Editing who an agent looks for, or which LinkedIn account it uses, is refused without an active subscription.
