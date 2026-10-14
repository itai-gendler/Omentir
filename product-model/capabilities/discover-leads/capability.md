---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/lib/server/automation.ts#runAgents
- kind: code
  role: implementation
  target: src/lib/server/people-engine.ts#runPeopleEngineForAgent
- kind: code
  role: implementation
  target: src/lib/server/lead-qualification.ts
- kind: code
  role: implementation
  target: src/lib/server/data.ts#markAgentRun
---

# Discover leads

Every day at its run time each active agent looks for new leads through its sending LinkedIn account. A classic agent searches LinkedIn for its job titles, industries, keywords and locations; a Steal Customers agent reads recent posts by its competitor pages and their founders and employees and the people engaging with them. An AI model scores each person against the company profile, and only good fits are saved. The User watches the results on AI Agents and Leads.
