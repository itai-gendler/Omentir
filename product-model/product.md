---
id: omentir
summary: 'An AI sales workspace for LinkedIn: agents find and score prospects, run human-paced connection and message sequences from your own LinkedIn account, and handle replies until a lead is interested or books a meeting.'
category: sales-outreach
tags:
- linkedin
- outreach
- lead-generation
- ai-agents
authors:
- name: Vansh Yadav
  url: https://github.com/vanshyadav1408
license: MIT
languages:
- en
limitations:
- Omentir reaches LinkedIn only through the person's own connected LinkedIn account, and every invitation and message is sent as that person.
- Automated outreach stays inside each workspace's daily invitation and message limits and spaces out actions on every LinkedIn account; nothing is sent in bulk.
- AI never writes connection invitation notes; a note goes out only when the user wrote it.
- A workspace belongs to one person; workspaces are not shared with teammates.
- A self-hosted install relies on its operator's own database, LinkedIn connection service and AI model accounts, and its outreach stays a dry run until the operator enables live sending.
references:
- kind: doc
  role: intent
  target: README.md
  title: README
- kind: code
  role: implementation
  target: src/lib/server/types.ts
- kind: code
  role: implementation
  target: src/app/sidebar.tsx
- kind: doc
  role: context
  target: LICENSE
  title: License
---

# Omentir

Omentir is an AI sales workspace for finding qualified LinkedIn prospects,
drafting contextual outreach, running human-paced campaigns and handling
replies. A person describes the company they sell for, connects their LinkedIn
account, and starts AI agents that find and score matching people into lead
groups every day. Agents can also run a connection-and-message sequence on
those leads, written by the person or by AI, and keep answering replies until
the lead shows interest or books a meeting. The same workspace is open to the
person's own AI apps and coding agents through an agent API.

The same code runs as the hosted service and as a self-hosted install; the
hosted service adds accounts, subscriptions and billing, while a self-hosted
install is one operator's workspace behind an access password.

## Intent

Find qualified LinkedIn prospects, draft contextual outreach, run human-paced
campaigns and handle replies, while the people who use it own the code and can
run it on their own infrastructure.
