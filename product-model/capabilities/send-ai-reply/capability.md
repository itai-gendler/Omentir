---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#draftCampaignReplyMessage
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#shouldShareBookingLink
---

# Send AI reply

When a lead's AI answer is due Omentir asks an AI model for a reply from the conversation, the reply's intent, the company profile and pricing details, and the campaign's goal and tone, and sends it. When the campaign continues until booked and the lead shows interest or asks about pricing, the answer shares the booking link. AI answers ignore the send window, since the lead is waiting.
