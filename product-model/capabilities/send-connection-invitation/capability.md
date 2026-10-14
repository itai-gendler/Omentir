---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
- kind: code
  role: implementation
  target: src/lib/server/send-schedule.ts#isWithinSendWindow
- kind: code
  role: implementation
  target: src/lib/server/lead-time-zone.ts#sendWindowTimeZoneForLead
- kind: code
  role: implementation
  target: src/lib/server/data.ts#claimActionSlot
- kind: code
  role: implementation
  target: src/lib/server/automation-safety.ts#getAutomationSafetyMode
---

# Send connection invitation

When a lead's invitation step is due Omentir sends a LinkedIn connection invitation from the campaign's sending account, inside the campaign's send window on the lead's own clock, within the workspace's daily invite limit and spaced from the account's other actions.
