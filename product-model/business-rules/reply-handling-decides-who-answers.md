---
appliesTo:
- type: capability
  id: record-lead-reply
- type: capability
  id: send-ai-reply
references:
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#shouldStopForReply
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#shouldShareBookingLink
---

# The campaign's reply handling decides when AI stops answering a lead

Stop after the first reply hands every reply to the User. Continue until interest lets AI answer until hot interest. Continue until booked lets AI answer, share the booking link once interest shows, and stop when the lead confirms a meeting. Under every setting a negative, not-now or out-of-office reply, or a confirmed meeting, ends AI answers.
