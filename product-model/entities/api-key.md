---
domain: api
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#AgentApiKey
- kind: code
  role: implementation
  target: src/lib/server/data.ts#createAgentApiKey
---

# API key

A key that lets a Connected AI app work in a workspace through the agent API. Keys the User creates and keys issued when they approve an AI app work the same way.

## Information kept

- **Label** — the name the User gave it, or the AI app's name
- **Key prefix** — the first characters, to recognise it
- **Created** — when it was created
- **Last used** — when an AI app last used it

## States

### Active

AI apps can use it.

### Revoked

It no longer works.
