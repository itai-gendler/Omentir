---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: src/lib/server/agent-api.ts#requireAgentApiContext
- kind: code
  role: implementation
  target: src/lib/agent-tools.ts
- kind: doc
  role: intent
  target: README.md
  title: 'README: Connect from other AI apps'
---

# Connected AI app

The User's own AI app, coding agent or script that works in a workspace through the agent API, with an API key the User created or approved. It acts for the User who connected it.
