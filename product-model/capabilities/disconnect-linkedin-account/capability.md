---
domain: settings
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#disconnectLinkedInAccountActionImpl
- kind: code
  role: implementation
  target: src/lib/server/linkedin-accounts.ts#listVerifiedLinkedInAccounts
---

# Disconnect LinkedIn account

The User disconnects a LinkedIn account, ending its session at the LinkedIn connection service. Omentir also marks an account disconnected when it finds its LinkedIn session has ended.
