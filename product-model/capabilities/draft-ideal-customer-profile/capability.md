---
domain: ai-agents
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#draftAgentSetupActionImpl
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#draftAgentSetupWithGemini
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#draftAgentSetupResource
---

# Draft ideal customer profile

While setting up an agent the User asks AI to suggest who to look for. Omentir asks an AI model to draft a prospect description, job titles, industries, locations and keywords from the company profile and fills them into the setup for the User to change; nothing is saved until the agent is launched.
