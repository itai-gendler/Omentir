---
appliesTo:
- type: capability
  id: send-sequence-message
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts
---

# AI-written sequences send at most three messages to a lead who has not replied

After the third unanswered AI message the lead's outreach stops and the end is recorded; the User is not emailed about silence. Campaigns that stop after the first reply and messages the User wrote are not counted toward it.
