---
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#completeOnboardingQuestionsActionImpl
- kind: code
  role: implementation
  target: src/app/actions.ts#completeSelfHostedOnboardingActionImpl
- kind: code
  role: implementation
  target: src/app/onboarding/step-questions.tsx
---

# Answer onboarding questions

On the hosted service a new User answers four questions: how they heard of Omentir, their role, their company size and their goal. A self-hosted install skips the questions.
