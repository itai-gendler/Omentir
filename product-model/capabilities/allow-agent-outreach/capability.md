---
domain: ai-agents
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#allowOutreachOnAgent
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
---

# Allow agent outreach

The User lets a leads-only agent's leads be contacted again by the campaigns on its lead group. Outreach that ended while it was leads only stays ended.
