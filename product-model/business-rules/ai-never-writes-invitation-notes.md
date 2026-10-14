---
appliesTo:
- type: capability
  id: send-connection-invitation
- type: capability
  id: create-agent
- type: capability
  id: edit-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/campaign-sequence.ts#campaignStepsFromActions
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
---

# AI never writes a connection invitation note

An invitation carries a note only when the User wrote one and it reads cleanly with the lead's details filled in; otherwise the invitation goes without a note.
