---
actors:
- visitor
access: public
entryPoints:
- web-app: /login
references:
- kind: code
  role: implementation
  target: src/app/login/page.tsx
- kind: code
  role: implementation
  target: src/app/signup/page.tsx
---

# Sign in

Where a Visitor signs in, or on the hosted service creates an account.
