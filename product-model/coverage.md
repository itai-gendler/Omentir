---
scope: The Omentir web app, its agent API and MCP connector, its LinkedIn event and job routes, and the server code behind them.
method: Static reading of source, README and agent docs at the pinned commit; nothing was run.
covered:
- description: Signed-in app pages, the app shell and the server actions behind them.
  paths:
  - src/app/(app)/
  - src/app/actions.ts
  - src/app/sidebar.tsx
  - src/app/workspace-switcher.tsx
  - src/app/delete-workspace-card.tsx
  - src/app/delete-workspace-dialog.tsx
  - src/app/workspace-time-zone.tsx
  - src/app/use-sidebar-resource.ts
  - src/app/api/app/sidebar-data/
- description: Sign-in, sign-up, onboarding, plans, LinkedIn connect and AI app consent pages and routes.
  paths:
  - src/app/login/
  - src/app/signup/
  - src/app/logout/
  - src/app/sso-callback/
  - src/app/setup/
  - src/app/local-login-form.tsx
  - src/app/auth-choice.tsx
  - src/app/onboarding/
  - src/app/website-fetch-panel.tsx
  - src/app/upgrade/
  - src/app/checkout/
  - src/app/subscription-creation-successful/
  - src/app/connect/
  - src/app/reconnect/
  - src/app/oauth/
  - src/app/api/local-auth/
  - src/app/api/connect/
  - src/app/api/oauth/
  - src/app/api/onboarding/
  - src/proxy.ts
- description: Agent API and MCP connector.
  paths:
  - src/app/api/agent/
  - src/lib/agent-tools.ts
  - src/lib/agent-api-token.ts
  - src/lib/agent-workspace-switch.ts
- description: LinkedIn event webhook and the automation job route.
  paths:
  - src/app/api/webhooks/unipile/
  - src/app/api/jobs/automation-tick/
- description: 'Server services: data, automation, discovery, reply handling, scheduling, AI drafting, billing state and LinkedIn accounts.'
  paths:
  - src/lib/server/
- description: Shared product rules used by the app and server.
  paths:
  - src/lib/
exclusions:
- description: Marketing site, blog, guides, comparisons, pricing page, SEO helpers and content management.
  paths:
  - src/app/page.tsx
  - src/app/blogs/
  - src/app/guides/
  - src/app/comparisons/
  - src/app/alternatives/
  - src/app/features/
  - src/app/integrations/
  - src/app/use-cases/
  - src/app/seo-content/
  - src/app/help/
  - src/app/[slug]/
  - src/app/about/
  - src/app/demo/
  - src/app/pricing/
  - src/app/minimum-booking-guarantee/
  - src/app/studio/
  - src/sanity/
  - src/lib/cms/
  - sanity.config.ts
  - sanity.cli.ts
- description: Machine-readable site files, legal pages and search engine helpers.
  paths:
  - src/app/llms.txt/
  - src/app/llms-full.txt/
  - src/app/agents.md/
  - src/app/agent.json/
  - src/app/page-markdown/
  - src/app/robots.ts
  - src/app/sitemap.ts
  - src/app/privacy-policy/
  - src/app/terms-of-service/
  - src/app/indexnow-key.txt/
  - src/app/8f3c1a9e6b24d0c75e18a4f2b9d63c07.txt/
- description: Internal operator statistics dashboard.
  paths:
  - src/app/stats/
  - src/lib/server/stats/
  - src/app/api/stats/
- description: Operational jobs for diagnostics and site icons.
  paths:
  - src/app/api/jobs/gemini-diagnostics/
  - src/app/api/jobs/workspace-favicons/
  - src/app/api/health/
  - src/app/api/webhooks/sanity/
- description: 'Remaining app-root code: landing page sections, shared UI components, AI app setup snippets and the root layout.'
  paths:
  - src/app/
- description: Styling, fonts, icons, static assets and editor agent configuration.
  paths:
  - src/app/globals.css
  - src/app/fonts/
  - src/app/ui/
  - public/
  - .cursor/
  - .grok/
  - .cursor-plugin/
  - plugins/
- description: Build, deployment, telemetry setup and repository tooling.
  paths:
  - Dockerfile
  - docker-compose.yml
  - production-build.sh
  - next.config.ts
  - scripts/
  - .github/
  - firebase.json
  - firestore.indexes.json
  - firestore.rules
  - src/instrumentation.ts
  - src/instrumentation-node.ts
  - package.json
  - bun.lock
unmapped:
- description: 'Free public tools: lead finder and LinkedIn profile rating.'
  paths:
  - src/app/tools/
  - src/app/api/tools/
- description: Billing provider and hosted sign-in provider webhooks.
  paths:
  - src/app/api/webhooks/whop/
  - src/app/api/webhooks/clerk/
  - src/app/billing/
  - src/app/api/billing/
- description: Public surveys and the mailing list.
  paths:
  - src/app/surveys/
  - src/app/api/surveys/
  - src/app/api/mailing-list/
  - src/app/api/jobs/mailing-list-backfill/
- description: Website analysis and preview endpoints used by the public site.
  paths:
  - src/app/api/website-analysis/
  - src/app/api/website-preview/
- description: Profile photo upload.
  paths:
  - src/app/api/app/avatar/
limitations: []
---

# Coverage
