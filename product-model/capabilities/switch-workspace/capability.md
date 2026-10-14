---
domain: workspace
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#switchWorkspaceActionImpl
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#switchWorkspaceResource
- kind: code
  role: implementation
  target: src/lib/agent-workspace-switch.ts#agentWorkspaceSwitchDenied
- kind: code
  role: implementation
  target: src/lib/server/data.ts#setAgentApiKeyWorkspace
---

# Switch workspace

The User, or their Connected AI app, moves to another of the User's workspaces. In the app every page then shows that workspace; through the agent API the key itself moves, so later calls work there.
