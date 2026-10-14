---
appliesTo:
- type: capability
  id: create-agent
- type: capability
  id: edit-agent
- type: capability
  id: edit-workspace-profile
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#bookingLinkFromForm
- kind: code
  role: implementation
  target: src/lib/scheduling-link.ts
---

# A campaign that continues until booked always has a booking link

Its own booking link, or the workspace's demo booking link when it has none. A new demo booking link is copied onto until-booked campaigns that have no link of their own or still had the previous one.
