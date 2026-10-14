---
appliesTo:
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: send-ai-reply
- type: capability
  id: run-action-now
- type: capability
  id: send-linkedin-message
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#claimActionSlot
- kind: code
  role: implementation
  target: src/lib/server/send-schedule.ts
---

# Automated actions on one LinkedIn account are at least five minutes apart

Invitations, sequence messages and AI answers from one LinkedIn account share one drip of at most one action every five minutes, also across Send now; a message the User sends pushes the next automated action back.

## Rationale

LinkedIn restricts accounts whose activity looks automated.
