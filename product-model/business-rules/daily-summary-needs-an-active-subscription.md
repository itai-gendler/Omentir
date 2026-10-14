---
appliesTo:
- type: entity
  id: workspace
  effect: changes
  facts:
  - Daily summary
permits:
- related:
  - {verb: owns, entity: user}
  when:
  - {entity: user, fact: Subscription status, is: Active}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#saveSettingsActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateWorkspaceBilling
---

# Only the workspace's owner turns the daily summary on, and only with an active subscription

The daily summary is a paid feature; when a subscription is cancelled or expires, the summary is turned off on every workspace the User owns.
