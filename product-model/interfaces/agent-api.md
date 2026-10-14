---
type: agent
actors:
- ai-agent
entryPoints:
- agent: /api/agent/v1/mcp
- agent: /api/agent/v1/openapi.json
references:
- kind: code
  role: implementation
  target: src/app/api/agent/v1/mcp/route.ts
- kind: code
  role: implementation
  target: src/lib/agent-tools.ts
- kind: code
  role: implementation
  target: src/app/api/agent/v1/openapi.json/route.ts
- kind: code
  role: implementation
  target: src/lib/server/agent-api.ts#requireAgentApiContext
- kind: doc
  role: intent
  target: README.md
  title: 'README: Connect from other AI apps'
---

# Agent API

The tools a Connected AI app calls to work in a workspace: an MCP connector, and the same operations as plain HTTP endpoints. Every call carries an API key and works in that key's workspace.
