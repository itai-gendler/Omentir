---
appliesTo:
- type: capability
  id: send-linkedin-message
- type: entity
  id: linkedin-chat
references:
- kind: code
  role: implementation
  target: src/app/actions.ts#sendLinkedInChatMessageActionImpl
---

# A reply in a LinkedIn chat is sent only from the LinkedIn account that owns that chat

So a User with several connected accounts never answers from the wrong identity.
