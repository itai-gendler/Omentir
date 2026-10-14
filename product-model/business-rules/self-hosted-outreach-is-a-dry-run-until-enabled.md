---
appliesTo:
- type: capability
  id: send-connection-invitation
- type: capability
  id: send-sequence-message
- type: capability
  id: send-ai-reply
- type: capability
  id: run-action-now
- type: capability
  id: discover-leads
references:
- kind: code
  role: implementation
  target: src/lib/server/automation-safety.ts#getAutomationSafetyMode
- kind: doc
  role: intent
  target: README.md
  title: 'README: Enable automation safely'
---

# A self-hosted install sends nothing to LinkedIn until its operator enables live sending

Until then each automated decision is recorded as what would have been sent, and Send now is refused. The operator can also stop all automation at once.
