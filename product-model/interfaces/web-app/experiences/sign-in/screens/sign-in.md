---
entryPoints:
- web-app: /login
references:
- kind: code
  role: implementation
  target: src/app/login/page.tsx
- kind: code
  role: implementation
  target: src/app/local-login-form.tsx
---

# Sign in

Where a Visitor signs in: with their account on the hosted service, or with the instance's access password on a self-hosted install.
