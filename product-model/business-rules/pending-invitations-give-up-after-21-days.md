---
appliesTo:
- type: capability
  id: mark-invitation-accepted
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
---

# A lead's outreach ends when their invitation is still pending after 21 days

One last check is made on the 21st day; an unaccepted invitation ends that lead's outreach.
