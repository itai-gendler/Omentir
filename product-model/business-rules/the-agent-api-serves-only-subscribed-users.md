---
appliesTo:
- type: context
  context: {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/lib/server/agent-api.ts#requireAgentApiContext
- kind: code
  role: implementation
  target: src/lib/agent-workspace-switch.ts#agentWorkspaceSwitchDenied
---

# The agent API answers only for a User with an active subscription

Every call needs an active API key, and the key's workspace owner must have an active subscription; otherwise the call is refused. A self-hosted install's keys work only in its one workspace.
