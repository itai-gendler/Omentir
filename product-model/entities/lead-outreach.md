---
references:
- kind: code
  role: implementation
  target: src/lib/server/types.ts#CampaignEnrollment
- kind: code
  role: implementation
  target: src/lib/server/scheduled-actions.ts#listScheduledActions
---

# Lead outreach

One lead's progress through one campaign: the step they are on, when the next action is due, and what is about to be sent.

## Information kept

- **Current step** — the campaign step the lead is on
- **Next action at** — when the next invitation or message is due
- **Your messages** — messages the User wrote for this lead, sent word for word in place of the campaign's
- **Prepared message** — the AI message drafted ahead during a wait, sent as shown
- **Invitation sent at** — when the connection invitation went out
- **Blocked reason** — why the next action cannot go out

## States

### Queued

Waiting for its first action.

### Invitation sent

The invitation is out and the lead has not accepted yet.

### Connected

The lead accepted, or was already a connection.

### Message sent

A sequence message went out.

### Reply received

The lead replied and AI will answer.

### Replied

The lead replied; AI answered, or the conversation was handed to the User.

### Stopped

Outreach for this lead ended and sends nothing more.

### Error

An action could not go out; it is retried later or needs the cause fixed.
