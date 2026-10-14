---
availability:
- {place: 'web-app::app'}
- {place: linkedin-events}
references:
- kind: code
  role: implementation
  target: src/lib/server/inbound.ts#applyConnectionAccepted
- kind: code
  role: implementation
  target: src/lib/server/inbound.ts#applyAcceptanceIfFirstDegree
- kind: code
  role: implementation
  target: src/app/api/webhooks/unipile/route.ts#POST
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
---

# Mark invitation accepted

Omentir learns that a lead accepted the invitation, from the LinkedIn connection service's event or from a check of the account's invitations every two hours, and moves the lead's outreach on to messaging. An invitation still pending after 21 days ends the lead's outreach.
