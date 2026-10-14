---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/(app)/settings/sign-out-button.tsx
- kind: code
  role: implementation
  target: src/app/logout/route.ts#GET
- kind: code
  role: implementation
  target: src/app/api/local-auth/logout/route.ts#POST
---

# Sign out

The User ends their session on this device.
