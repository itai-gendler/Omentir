---
availability:
- {place: 'web-app::sign-in'}
references:
- kind: code
  role: implementation
  target: src/app/login/page.tsx
- kind: code
  role: implementation
  target: src/app/local-login-form.tsx
- kind: code
  role: implementation
  target: src/app/api/local-auth/login/route.ts#POST
- kind: code
  role: implementation
  target: src/lib/runtime-mode.ts#isLocalPasswordRequired
- kind: doc
  role: intent
  target: README.md
  title: 'README: Access control (local login)'
---

# Sign in

A Visitor signs in to the app. How depends on the install: the hosted service signs people in with their Omentir account, and a self-hosted install asks for the access password its operator configured, or lets anyone in when the operator explicitly opened it.
