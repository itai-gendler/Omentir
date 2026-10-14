---
appliesTo:
- type: capability
  id: pause-agent
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: send-ai-reply
- type: capability
  id: resume-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runEnrollment
- kind: code
  role: implementation
  target: src/lib/server/data.ts#resumeAgent
---

# While an agent is paused, nothing automated reaches the leads it found

Invitations, follow-ups and AI answers to its leads wait in every campaign and resume when the agent is resumed. Deleting the agent ends them instead.
