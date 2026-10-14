---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/api/onboarding/lead-preview/route.ts#POST
- kind: code
  role: implementation
  target: src/lib/server/gemini.ts#findPreviewLeadsWithGemini
- kind: code
  role: implementation
  target: src/app/onboarding/step-lead-preview.tsx
---

# Preview leads

During onboarding Omentir asks an AI model for example buyers that match the company profile, to show what an agent would find. The examples are shown, not kept.
