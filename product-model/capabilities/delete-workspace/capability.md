---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#deleteWorkspaceActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#deleteOwnedWorkspace
- kind: code
  role: implementation
  target: src/app/delete-workspace-dialog.tsx
---

# Delete workspace

The User deletes a workspace with everything in it: company profile, agents, leads and campaigns. Outreach stops first. Deleting the User's first workspace empties it instead, because their account and billing live there.
