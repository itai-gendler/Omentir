---
entities:
- entity: workspace
  shows:
  - Name
  collects:
  - Name
entryPoints:
- web-app: /oauth/authorize
references:
- kind: code
  role: implementation
  target: src/app/oauth/authorize/page.tsx
- kind: code
  role: implementation
  target: src/app/api/oauth/authorize/decision/route.ts#POST
---

# Connect workspace

Where the User approves an AI app's request to work in one of their workspaces.
