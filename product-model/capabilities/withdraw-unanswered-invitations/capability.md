---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/linkedin-health.ts#runInviteWithdrawals
- kind: code
  role: implementation
  target: src/lib/linkedin-health.ts
---

# Withdraw unanswered invitations

Every two hours Omentir withdraws connection invitations that have waited longer than the workspace's invite withdrawal setting, a few at a time and at most fifty a day per LinkedIn account, so unanswered invitations do not pile up. LinkedIn then blocks inviting those people again for about three weeks.
