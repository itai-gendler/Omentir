---
domain: ai-agents
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#setAgentLeadsOnlyActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#setAgentLeadsOnly
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
---

# Make agent leads only

The User makes an agent leads only. It keeps finding leads, but Omentir stops contacting everyone it found, in every lead group; sequences and AI replies already running for those people end.
