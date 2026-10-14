---
availability:
- {place: 'web-app::app'}
- {place: linkedin-events}
references:
- kind: code
  role: implementation
  target: src/app/api/connect/linkedin/route.ts#GET
- kind: code
  role: implementation
  target: src/app/api/connect/callback/route.ts#POST
- kind: code
  role: implementation
  target: src/lib/server/data.ts#saveLinkedInAccount
- kind: code
  role: implementation
  target: src/app/connect/success/page.tsx
- kind: doc
  role: intent
  target: README.md
  title: 'README: LinkedIn connect notify callback'
---

# Connect LinkedIn account

The User connects a LinkedIn account by signing in to LinkedIn through the LinkedIn connection service, which then tells Omentir the account is connected. The same flow reconnects an account whose session ended.
