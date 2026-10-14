---
entities:
- entity: workspace
  shows:
  - Website
  - Company name
  - Description
  - Buyer profile
  collects:
  - Website
  - Onboarding answers
- entity: user
  shows:
  - Subscription status
entryPoints:
- web-app: /onboarding
references:
- kind: code
  role: implementation
  target: src/app/onboarding/page.tsx
- kind: code
  role: implementation
  target: src/app/onboarding/step-lead-preview.tsx
- kind: code
  role: implementation
  target: src/app/onboarding/step-questions.tsx
- kind: code
  role: implementation
  target: src/app/onboarding/step-upgrade.tsx
---

# Onboarding

The first-run setup: fetch the company website, preview example buyers, answer a few questions, then choose a plan. Each stage opens only once the one before it is done.
