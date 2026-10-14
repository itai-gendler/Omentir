---
appliesTo:
- type: capability
  id: record-lead-reply
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#claimLeadOutcomeNotification
- kind: code
  role: implementation
  target: src/lib/server/data.ts#claimReplyNotification
---

# The User is emailed once per lead for interest and once for a booked meeting

Reply, interest and meeting emails go to the workspace's notification email only while the User's subscription is active, and a repeated event never sends the same email twice.
