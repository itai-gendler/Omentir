---
domain: overview
availability:
- {place: 'web-app::app'}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#setAverageTicketSizeActionImpl
- kind: code
  role: implementation
  target: src/lib/server/data.ts#setAverageTicketSize
---

# Set deal size

The User sets the workspace's average deal size from Overview, so the pipeline is shown as money.
