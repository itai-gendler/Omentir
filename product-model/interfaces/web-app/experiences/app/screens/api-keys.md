---
entities:
- entity: api-key
  shows:
  - Label
  - Key prefix
  - Created
  - Last used
  collects:
  - Label
entryPoints:
- web-app: /api-keys
references:
- kind: code
  role: implementation
  target: src/app/(app)/api-keys/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/api-keys/api-keys-view.tsx
---

# API

The workspace's API keys and how to connect AI apps to the workspace.
