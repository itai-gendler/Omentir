---
domain: api
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/oauth/authorize/page.tsx
- kind: code
  role: implementation
  target: src/app/api/oauth/authorize/decision/route.ts#POST
- kind: code
  role: implementation
  target: src/app/api/oauth/token/route.ts#POST
- kind: doc
  role: intent
  target: README.md
  title: 'README: Connect from other AI apps'
---

# Connect AI app

When the User adds Omentir to a chat app such as their AI assistant, the app asks for access and the User approves Connect workspace for one of their workspaces. Omentir then issues an API key named after the app, with no key to copy.
