---
domain: overview
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/(app)/overview/overview-view.tsx
- kind: code
  role: implementation
  target: src/app/(app)/overview/overview-setup.tsx
- kind: code
  role: implementation
  target: src/lib/server/workspace-setup.ts#getWorkspaceSetup
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#getWorkspaceStatsResource
---

# View outreach results

The User, or their Connected AI app, reads the workspace's results for a period: hot opportunities, invitations and messages sent, the pipeline value and activity over time. Until the workspace is set up, Overview shows the setup checklist instead.
