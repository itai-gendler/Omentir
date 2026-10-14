---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
- kind: code
  role: implementation
  target: src/app/(app)/agents/(list)/page.tsx
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#listAgentResources
---

# Browse agents

The User, or their Connected AI app, reads the workspace's agents: each one's type and status, what it found and contacted, accept and reply rates, and what it does next. Without an active subscription the agents are shown as stopped.
