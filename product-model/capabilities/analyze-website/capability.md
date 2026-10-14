---
domain: workspace
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#analyzeWebsiteActionImpl
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#analyzeWebsiteOrSearch
- kind: code
  role: implementation
  target: src/lib/server/agent-api-actions.ts#analyzeWebsiteResource
---

# Analyze website

Omentir asks an AI model to read the company's website and fills the company profile from it: what the product does, the buyers and their pain points, pricing and selling points. It runs when the User fetches their website during onboarding or on the Workspace page, or when their AI app asks.
