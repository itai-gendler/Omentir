---
entities:
- entity: agent
  shows:
  - Name
  - Type
  - Leads only
  - Next run
  - Last run
- entity: lead-group
  shows:
  - Name
  - Lead count
- entity: lead
  shows:
  - Source agent
- entity: lead-outreach
  shows:
  - Invitation sent at
entryPoints:
- web-app: /agents
references:
- kind: code
  role: implementation
  target: src/app/(app)/agents/(list)/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
---

# AI Agents

Every agent in the workspace with its status, what it found and contacted, and what it does next.
