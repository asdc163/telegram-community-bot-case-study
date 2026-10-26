# Telegram Community Bot

An anonymized commercial engineering case study by Tommy. I used AI-assisted development to build Telegram workflows for community participation, owner management, and service handoff.

**Public material:** documentation and conceptual diagrams. Commercial source, bot identities, customer groups, and operating data remain private.

[繁體中文](README.zh-TW.md) · [Architecture and decisions](docs/architecture.md) · [Verification scope](docs/verification.md) · [Portfolio](https://github.com/asdc163/ai-builder-portfolio)

## The product problem

Members should be able to participate where the community already talks. Sensitive settings belong in the owner's private conversation. A bot also needs to handle stale menus, role changes, repeated updates, and delivery failures without confusing participation with permission to manage.

## My work

I worked on product and interaction flows, TypeScript services, role checks, persistent delivery, rule-based moderation, regression work, and owner-transfer packaging. The stack included Node.js, TypeScript, Fastify, PostgreSQL, and Docker.

## What mattered in the implementation

Member participation stays in the group. The current group owner manages settings and activities in private messages; sensitive actions recheck the current Telegram role, so an old menu cannot retain authority after ownership changes.

Delivery uses persistent state. A rate limit can be deferred, a known failure can be recorded, and an unknown send outcome needs review. Automatically retrying every uncertain result risks a duplicate message.

Moderation distinguishes current roles and message provenance rather than trusting a bot name or a familiar-looking button. The service also needs the relevant Telegram permissions; it cannot inspect messages Telegram never delivers to it.

For handoff, stopping the old runtime, preserving the encryption material, and checking a restored database matter as much as copying source files. Platform ownership and application ownership must be reconciled separately.

## Recorded delivery state

Private records describe automated regressions, role checks through the Telegram API, selected native Telegram journeys, and transfer-package validation. Some later behavior changes did not receive a fresh client UI walkthrough. These evidence layers are kept separate in [verification scope](docs/verification.md).

The case was reviewed against those records on 2026-10-27. Recipient deployment, all device and language flows, live payment acceptance, and continuous hosting are not established by this publication.

## AI's role

AI assisted the engineering work. The bot behaviors described here are deterministic and rule-based. There is no claim of LLM moderation or an autonomous AI community manager.

This repository has no runnable commercial application or live bot link. See [disclosure boundaries](DISCLOSURE.md).
