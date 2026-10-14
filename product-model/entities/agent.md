---
domain: ai-agents
relations:
- entity: lead
  verb: found
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Agent
- kind: code
  role: implementation
  target: src/app/(app)/agents/agents-view.tsx
---

# Agent

An AI agent that works for a workspace: it finds and scores people into its lead group every day, and unless it is leads only, its campaign contacts them. Its type says how it works: Leads only, Leads + outreach, Outreach only (people imported from a CSV, no discovery) or Steal Customers (people who comment on competitors' LinkedIn posts).

## Information kept

- **Name** — the agent's name, shown on its card
- **Type** — Leads only, Leads + outreach, Outreach only or Steal Customers
- **Prospect description** — the ideal customer the agent looks for, in the User's words
- **Job titles** — titles the agent searches for
- **Industries** — industries the agent targets
- **Locations** — where the people must be
- **Keywords** — keywords the agent searches with
- **Competitor pages** — competitor company pages and founder or employee profiles a Steal Customers agent watches
- **Sending account** — the LinkedIn account the agent searches and sends with
- **Leads only** — whether the people it finds are kept out of every outreach
- **Daily run time** — the time of day it looks for leads: the time it was created
- **Next run** — when it next looks for leads
- **Last run** — when it last looked for leads

## States

### Active

The agent looks for leads at its daily run time and its leads' outreach runs.

### Running

The agent is looking for leads right now.

### Paused

The agent finds nobody and every automated touch to the leads it found waits.

### Error

The last search failed; the agent tries again at its next daily run.
