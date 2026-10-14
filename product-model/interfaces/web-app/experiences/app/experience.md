---
actors:
- user
access: authenticated
entryPoints:
- web-app: /overview
references:
- kind: code
  role: implementation
  target: src/app/(app)/layout.tsx
---

# App

The signed-in app. Everything in it belongs to the User's active workspace.
