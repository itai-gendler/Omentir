---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#resumeAgentActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#resumeAgent
---

# Resume agent

The User, or their Connected AI app, switches a paused or failed agent back on. It looks for leads once right away, then at its usual daily time, and the outreach that waited for it carries on.
