---
type: web
actors:
- visitor
- user
languages:
- en
entryPoints:
- web: /login
- web: /overview
references:
- kind: code
  role: implementation
  target: src/app/(app)/layout.tsx
- kind: code
  role: implementation
  target: src/app/sidebar.tsx
---

# Web app

The Omentir web application: the sign-in pages, and the signed-in app where the User sets up workspaces, agents and LinkedIn, and works their leads and messages.
