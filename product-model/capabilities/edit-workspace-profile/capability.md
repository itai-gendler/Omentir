---
availability:
- {place: 'web-app::app'}
- {place: agent-api}
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#saveProductProfileActionImpl
- kind: code
  role: implementation
  target: src/lib/scheduling-link.ts#normalizeSchedulingLink
- kind: code
  role: implementation
  target: src/lib/server/agent-api-operations.ts#updateProductProfileResource
- kind: code
  role: implementation
  target: src/app/(app)/my-product/product-view.tsx
---

# Edit workspace profile

The User edits the company profile AI uses to find buyers and write outreach: company details, pain points, pricing details, selling points, the buyer profile, the demo booking link and the deal size. The booking link can also be added from the Overview checklist, and company information from agent setup.
