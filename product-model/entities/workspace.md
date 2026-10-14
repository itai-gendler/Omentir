---
relations:
- entity: linkedin-account
  verb: connects
  cardinality: one-to-many
- entity: agent
  verb: runs
  cardinality: one-to-many
- entity: lead-group
  verb: contains
  cardinality: one-to-many
- entity: api-key
  verb: issues
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Workspace
- kind: code
  role: implementation
  target: src/lib/server/types.ts#ProductProfile
- kind: code
  role: implementation
  target: src/lib/server/types.ts#WorkspaceSettings
---

# Workspace

One company the User sells for: its company profile, which AI uses to find buyers and write outreach, its sending settings, and everything its agents find and send. A User can keep several workspaces and switches between them.

## Information kept

- **Name** — shown in the workspace switcher; taken from the company name
- **Icon** — the icon of the company's website
- **Website** — the company's landing page
- **Company name** — the company the outreach is sent for, with its industry and size
- **Description** — what the product does, in plain language
- **Pain points** — the problems buyers have that the product solves
- **Pricing details** — plain-language pricing facts AI may quote when a lead asks
- **Demo booking link** — the meeting scheduler link agents share when a campaign continues until a meeting is booked
- **Selling points** — key features and social proof AI may mention
- **Buyer profile** — who buys: use cases, target buyers, buyer titles, role words, industries, company sizes, keywords and preferred locations
- **Deal size** — the average deal size used to value the pipeline
- **Time zone** — the zone every date is shown in and daily limits reset in
- **Notification email** — where Omentir emails replies, interested leads, invitation pauses and the daily summary
- **Daily invite limit** — the most connection invitations sent per day, 1 to 100
- **Daily message limit** — the most LinkedIn messages sent per day, 1 to 200
- **First message delay** — how long after a connection is accepted the first message waits in a new sequence
- **Daily summary** — whether the daily outreach summary email is on; off until the User turns it on
- **Daily summary hour** — the local hour the daily summary is sent
- **Invite withdrawal** — after how many days unanswered connection invitations are withdrawn; 28 unless changed, 0 is off
- **Onboarding answers** — how the User heard of Omentir, their role, company size and goal
