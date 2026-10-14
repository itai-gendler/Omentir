---
domain: settings
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#saveSettingsActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateWorkspaceSettings
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateWorkspaceTimezone
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#updateWorkspaceSettingsResource
---

# Change workspace settings

The User, or their Connected AI app, changes the workspace's time zone, daily invitation and message limits, the first message delay, the daily summary and when unanswered invitations are withdrawn.
