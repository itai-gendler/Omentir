---
domain: leads
relations:
- entity: lead-outreach
  verb: goes through
  cardinality: one-to-many
- entity: conversation
  verb: has
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Lead
- kind: code
  role: implementation
  target: src/lib/server/data.ts#upsertLead
---

# Lead

A LinkedIn member an agent found, or the User imported, as a possible buyer. Each person is a lead once per workspace.

## Information kept

- **Name** — the person's name
- **Headline** — their job title
- **Company** — where they work
- **Location** — where they are; it also sets the clock their send window is read on
- **LinkedIn profile** — the link to their LinkedIn profile
- **Photo** — their profile photo
- **Summary** — what the agent learned about them
- **Fit score** — how well they match the workspace's buyer profile, 0 to 100
- **Score reasons** — why they are a good fit
- **Lead reason** — why the agent picked them
- **Engagement** — the competitor post and comment or reaction that surfaced them
- **Source agent** — the agent that found them first

## States

### New

Found and not contacted yet.

### Invited

A connection invitation was sent.

### Connected

They are a first-degree connection of the sending account.

### Messaged

At least one sequence message was sent.

### Replied

They wrote back, or AI answered them.

### Stopped

Outreach to them was stopped before it started, or because the User messaged them directly.
