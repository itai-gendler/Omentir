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
references:
- kind: code
  role: implementation
  target: src/lib/server/send-schedule.ts#isWithinSendWindow
- kind: code
  role: implementation
  target: src/lib/server/lead-time-zone.ts#sendWindowTimeZoneForLead
---

# Invitations and sequence messages go out only inside the campaign's send window on the lead's own clock

The window is read in the lead's time zone from their profile location, and the workspace's time zone when the location is unknown. AI answers to a lead who just wrote, and Send now, are not held to the window.
