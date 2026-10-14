---
relations:
- entity: lead-outreach
  verb: runs
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Campaign
- kind: code
  role: implementation
  target: src/lib/server/campaign-sequence.ts
---

# Campaign

The outreach sequence an agent runs on its lead group: a connection invitation, waits and messages, when it may send, and who owns the conversation once a lead replies.

## Information kept

- **Name** — the campaign's name
- **Steps** — the invitation (with an optional note the User wrote), the waits and the messages, each written by the User or by AI
- **Send window** — Business hours (Mon-Fri 9-6), Extended hours (every day 7-22) or Around the clock, read on each lead's local clock
- **When a lead replies** — Stop after the first reply, Continue until interest, or Continue until booked
- **Booking link** — the scheduler link shared when continuing until booked; the workspace's demo booking link unless overridden
- **Email me when a lead replies** — whether the User is emailed at each reply when the campaign stops after the first reply
- **Goal** — warm conversation or demo, fed to every AI message
- **Message tone** — how AI messages should sound
- **Sending account** — the LinkedIn account the campaign sends from
