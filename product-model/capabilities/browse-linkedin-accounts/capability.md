---
domain: settings
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/(app)/settings/linkedin-health-card.tsx
- kind: code
  role: implementation
  target: src/lib/server/linkedin-health.ts
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#listLinkedInAccountResources
---

# Browse LinkedIn accounts

The User, or their Connected AI app, reads the connected LinkedIn accounts and, in Settings, each account's health: pending invitations, acceptance rate and profile views today.
