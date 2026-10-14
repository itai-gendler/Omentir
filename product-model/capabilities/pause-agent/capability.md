---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#pauseAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#pauseAgent
---

# Pause agent

The User, or their Connected AI app, pauses an agent. It stops looking for leads, and every automated touch to the leads it found waits: invitations, follow-ups, acceptance checks and AI replies. Pausing works with or without an active subscription.
