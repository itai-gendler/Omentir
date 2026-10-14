---
appliesTo:
- type: entity
  id: agent
  effect: changes
  to: Active
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
- unattended: true
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#resumeAgentActionImpl
---

# Only the workspace's owner, or an AI app they connected, resumes an agent, and only with an active subscription

A paused or failed agent goes back to work only while the User's subscription is active; the Product itself returns an agent to Active after each run. Pausing needs no subscription.
