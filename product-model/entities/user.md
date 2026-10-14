---
kind: person
acts: external
relations:
- entity: workspace
  verb: owns
  cardinality: one-to-many
- entity: ai-agent
  verb: connects
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#WorkspaceBilling
- kind: code
  role: implementation
  target: src/lib/server/entitlements.ts#entitlementsFor
- kind: code
  role: implementation
  target: src/lib/server/data.ts#updateWorkspaceBilling
---

# User

The person who signs in to Omentir and owns its workspaces. On the hosted service each person has their own account; a self-hosted install has exactly one User, its operator.

## Information kept

- **Name** — the name shown in Settings
- **Email** — the address the User signs in with; it becomes a new workspace's notification email
- **Profile photo** — the photo shown in Settings
- **Subscription status** — Active while the User's paid or complimentary plan is current; otherwise Pending, Cancelled or Expired. A self-hosted install is always Active
- **Plan** — the subscribed plan, which sets how many LinkedIn accounts are included
- **Extra LinkedIn accounts** — paid LinkedIn accounts on top of the one the plan includes
