---
type: webhook
actors:
- linkedin-provider
references:
- kind: code
  role: implementation
  target: src/app/api/webhooks/unipile/route.ts#POST
- kind: code
  role: implementation
  target: src/app/api/connect/callback/route.ts#POST
---

# LinkedIn events

Where the LinkedIn connection service tells Omentir that a LinkedIn account was connected, that a lead wrote a message, or that an invitation was accepted.
