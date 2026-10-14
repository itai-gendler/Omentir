---
appliesTo:
- type: capability
  id: connect-linkedin-account
- type: entity
  id: linkedin-account
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#saveLinkedInAccount
---

# A LinkedIn account is connected for one User only

Connecting a LinkedIn account that is already connected to another person's workspace is refused; the User's own workspaces share their LinkedIn accounts.
