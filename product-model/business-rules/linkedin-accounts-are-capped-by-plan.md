---
appliesTo:
- type: capability
  id: connect-linkedin-account
- type: capability
  id: add-extra-linkedin-accounts
references:
- kind: code
  role: implementation
  target: src/lib/plan-limits.ts#billedLinkedInAccountLimit
- kind: code
  role: implementation
  target: src/lib/server/linkedin-accounts.ts#enforceLinkedInAccountCap
---

# A User connects at most as many LinkedIn accounts as their plan and extra LinkedIn accounts allow

Every plan includes one LinkedIn account; extra LinkedIn accounts raise the limit. A self-hosted install has no limit. When the limit drops, the newest accounts beyond it are disconnected.
