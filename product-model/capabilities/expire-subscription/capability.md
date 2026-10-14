---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#purgeExpiredUnipileAccounts
- kind: code
  role: implementation
  target: src/lib/server/linkedin-accounts.ts#purgeWorkspaceUnipileAccounts
---

# Expire subscription

On the hosted service, when a User's paid period ends without renewal Omentir marks the subscription expired, drops the extra LinkedIn accounts and disconnects the User's LinkedIn accounts. Agents and outreach then wait until the User subscribes again.
