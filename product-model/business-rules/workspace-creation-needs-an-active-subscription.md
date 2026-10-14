---
appliesTo:
- type: entity
  id: workspace
  effect: creates
  contexts:
  - {place: 'web-app::app'}
permits:
- actors:
  - user
  when:
  - {entity: user, fact: Subscription status, is: Active}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#createWorkspaceActionImpl
---

# Only a User with an active subscription adds a workspace

Adding a workspace from the switcher is refused without an active subscription. The first workspace comes with the account.
