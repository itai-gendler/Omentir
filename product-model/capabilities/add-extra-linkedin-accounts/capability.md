---
domain: settings
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/checkout/seats/route.ts#GET
- kind: code
  role: implementation
  target: src/app/(app)/settings/linkedin-seats-card.tsx
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateWorkspaceLinkedInSeats
---

# Add extra LinkedIn accounts

On the hosted service a subscribed User pays for LinkedIn accounts beyond the one their plan includes, so more accounts can be connected.
