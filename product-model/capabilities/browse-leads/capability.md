---
domain: leads
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/(app)/leads/leads-view.tsx
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#listLeadResources
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#getLeadResource
---

# Browse leads

The User, or their Connected AI app, reads the workspace's leads by lead group: who each person is, their fit score and why they fit, and the post or comment that surfaced them.
