---
appliesTo:
- type: capability
  id: discover-leads
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: send-ai-reply
- type: capability
  id: run-action-now
- type: capability
  id: withdraw-unanswered-invitations
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runAgents
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#executeScheduledActionNow
---

# Agents search and campaigns send only while the User's subscription is active

Without it, discovery moves to the next day and outreach waits, rechecked hourly, until the User subscribes again. A self-hosted install is always subscribed.
