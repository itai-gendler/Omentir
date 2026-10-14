---
appliesTo:
- type: capability
  id: start-lead-outreach
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: make-agent-leads-only
- type: capability
  id: run-action-now
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#isSourcedByLeadsOnlyAgent
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
---

# People found by a leads-only agent are never invited or messaged automatically

Whatever lead group they end up in and whichever campaign contacts that group, a lead whose source agent is leads only gets no automated invitation, message or AI reply. A leads-only agent's lead group never gets a campaign.

## Rationale

The User picked Only Lead to contact those people themselves.
