---
entities:
- entity: user
  shows:
  - Subscription status
  - Plan
entryPoints:
- web-app: /upgrade
references:
- kind: code
  role: implementation
  target: src/app/upgrade/upgrade-view.tsx
- kind: code
  role: implementation
  target: src/app/checkout/route.ts#GET
---

# Plans

Where the User picks a plan and starts the subscription on the hosted service.
