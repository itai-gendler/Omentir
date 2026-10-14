---
entities:
- entity: workspace
  shows:
  - Name
  - Icon
  - Website
  - Company name
  - Description
  - Pain points
  - Pricing details
  - Demo booking link
  - Selling points
  - Buyer profile
  - Deal size
  collects:
  - Website
  - Company name
  - Description
  - Pain points
  - Pricing details
  - Demo booking link
  - Selling points
  - Buyer profile
  - Deal size
entryPoints:
- web-app: /workspace
references:
- kind: code
  role: implementation
  target: src/app/(app)/workspace/page.tsx
- kind: code
  role: implementation
  target: src/app/(app)/my-product/product-view.tsx
---

# Workspace

The company profile Omentir uses to find buyers and write outreach, filled from the website by AI and edited by the User.
