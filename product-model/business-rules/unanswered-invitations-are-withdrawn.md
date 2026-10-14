---
appliesTo:
- type: capability
  id: withdraw-unanswered-invitations
- type: capability
  id: change-workspace-settings
references:
- kind: code
  role: implementation
  target: src/lib/server/linkedin-health.ts#runInviteWithdrawals
- kind: code
  role: implementation
  target: src/lib/linkedin-health.ts
---

# Invitations pending longer than the workspace's invite withdrawal setting are withdrawn

28 days unless the User changes it, 0 turns it off. At most fifty are withdrawn a day per LinkedIn account, and only for subscribed workspaces. Withdrawing cannot be undone, and LinkedIn then blocks re-inviting the person for about three weeks.
