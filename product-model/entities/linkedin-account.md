---
relations:
- entity: linkedin-chat
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#LinkedInAccount
- kind: code
  role: implementation
  target: src/lib/server/data.ts#saveLinkedInAccount
- kind: code
  role: implementation
  target: src/lib/server/linkedin-health.ts
---

# LinkedIn account

A LinkedIn account the User connected so Omentir can search, invite and message as them. A LinkedIn account connected to one of the User's workspaces can be used from all of them.

## Information kept

- **Display name** — the LinkedIn member's name
- **Photo** — the LinkedIn profile photo
- **Connected on** — when it was connected
- **Health** — pending invitations, acceptance rate and profile views today

## States

### Connected

Omentir can act on LinkedIn through it.

### Disconnected

The User disconnected it or its LinkedIn session ended; connecting it again restores it.
