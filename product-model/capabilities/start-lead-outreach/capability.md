---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/data.ts#enrollNewLeadsInCampaign
- kind: code
  role: implementation
  target: src/lib/server/reply-automation-policy.ts#canEnrollLeadForOutreach
---

# Start lead outreach

Every few minutes Omentir starts outreach for each new lead in the lead group of an active campaign, so leads an agent finds later are contacted too. A person already contacted by another campaign, found by a leads-only agent, or whose agent is paused or deleted is not started.
