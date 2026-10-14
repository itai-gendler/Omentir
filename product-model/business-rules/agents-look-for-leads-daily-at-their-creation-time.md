---
appliesTo:
- type: capability
  id: discover-leads
- type: capability
  id: create-agent
- type: capability
  id: resume-agent
- type: capability
  id: edit-agent
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runAgents
- kind: code
  role: implementation
  target: src/lib/server/data.ts#nextDayAgentSlot
---

# Each agent looks for leads once a day at the time it was created, up to 75 new leads a day

A new or resumed agent runs right away, then at its daily time in the workspace's time zone. A run short of the day's target tries again 30 minutes later, up to four runs a day. Editing an agent never moves its daily time.
