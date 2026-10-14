---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#draftCampaignMessage
- kind: code
  role: implementation
  target: src/lib/server/inbound.ts#draftUpcomingMessagePreview
- kind: code
  role: implementation
  target: src/lib/server/owner-message-guard.ts#stopForOwnerMessage
---

# Send sequence message

When a connected lead's message step is due Omentir sends it: the message the User wrote for this lead, the campaign's written message with the lead's details filled in, or a message an AI model drafts from the lead's profile, the company profile, the campaign's goal and tone and the conversation so far. Messages respect the send window, the daily message limit and the account's spacing.
