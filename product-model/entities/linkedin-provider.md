---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: src/app/api/webhooks/unipile/route.ts#POST
- kind: code
  role: implementation
  target: src/app/api/connect/callback/route.ts#POST
---

# LinkedIn connection service

The service that holds connected LinkedIn sessions for Omentir. It tells Omentir when a LinkedIn account has been connected and delivers LinkedIn events: new messages and accepted invitations.
