---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/checkout/route.ts#GET
- kind: code
  role: implementation
  target: src/lib/server/billing-sync.ts#syncWorkspaceBillingIfInactive
- kind: code
  role: implementation
  target: src/app/upgrade/upgrade-view.tsx
---

# Subscribe

On the hosted service the User picks a plan and pays at checkout; Omentir then marks their subscription active, which every workspace they own shares. A self-hosted install has no subscription to buy.
