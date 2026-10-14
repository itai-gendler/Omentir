---
availability:
- {place: 'web-app::sign-in'}
references:
- kind: code
  role: implementation
  target: src/app/signup/page.tsx
- kind: code
  role: implementation
  target: src/lib/server/data.ts#ensureWorkspace
---

# Sign up

A Visitor creates an Omentir account on the hosted service, and Omentir gives them their first workspace. It exists only on the hosted service; a self-hosted install has one User and no sign-up.
