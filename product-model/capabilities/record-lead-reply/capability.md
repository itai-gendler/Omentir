---
availability:
- {place: 'web-app::app'}
- {place: linkedin-events}
references:
- kind: code
  role: implementation
  target: src/app/api/webhooks/unipile/route.ts#POST
- kind: code
  role: implementation
  target: src/lib/server/inbound.ts#persistInboundReply
- kind: code
  role: implementation
  target: src/lib/server/inbound.ts#finishInboundReplyClassification
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#shouldStopForReply
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#shouldArmAiReply
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#classifyReplyIntent
---

# Record lead reply

When a lead writes back, the LinkedIn connection service delivers the message, or Omentir finds it while checking each account's recent messages every five minutes. Omentir stores the reply, asks an AI model to read its intent, and applies the campaign's reply handling: stop and hand the conversation to the User, or let AI answer until interest or until a meeting is booked. It emails the User when the conversation is handed over, when interest is detected and when a meeting is booked.
