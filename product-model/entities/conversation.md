---
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#Conversation
- kind: code
  role: implementation
  target: src/lib/conversation-category.ts#conversationCategory
---

# Conversation

What Omentir has sent to a lead and what they replied, with AI's reading of their latest reply.

## Information kept

- **Messages** — every message sent and received, who sent it and when; sent ones are marked automated or written by the User
- **Reply intent** — AI's reading of the lead's reply: hot, meeting booked, warm, question, neutral, not now, negative or out of office
- **Intent reason** — why AI read the reply that way, and the suggested next step
- **Meeting booked at** — when the lead confirmed a meeting; it stays once set
- **Follow-up done at** — when the User marked the follow-up done
- **Category** — Successful, Interested, Needs a follow up or Denied, derived from the reply intent, a booked meeting and the follow-up mark
