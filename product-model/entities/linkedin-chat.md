---
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#LinkedInInboxThread
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#listInboxResource
---

# LinkedIn chat

A conversation in the connected LinkedIn account's own inbox, read live from LinkedIn.

## Information kept

- **Participant** — the other person's name, headline and profile
- **Messages** — the chat's messages, with attachments, reactions and InMail subjects
- **Unread** — whether it has unread messages
