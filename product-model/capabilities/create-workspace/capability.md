---
domain: workspace
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#createWorkspaceActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createOwnedWorkspace
- kind: code
  role: implementation
  target: src/app/workspace-switcher.tsx
---

# Create workspace

A User with an active subscription adds another workspace for another company they sell for. It starts with the first workspace's sending settings and opens on its company profile.
