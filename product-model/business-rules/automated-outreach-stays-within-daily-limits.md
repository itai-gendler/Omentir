---
appliesTo:
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: send-ai-reply
- type: capability
  id: send-linkedin-message
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#consumeDailyQuota
- kind: code
  role: implementation
  target: src/lib/server/data.ts#hasDailyQuotaRemaining
---

# Automated invitations and messages stay within the workspace's daily limits

Each local day in the workspace's time zone, automated invitations stay within the daily invite limit and messages, AI answers included, within the daily message limit. Messages the User writes count toward the day but are never blocked by it.
