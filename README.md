# Telegram community bot

A commercial bot for community activities and moderation. Members participate in their group; owners manage sensitive settings in private messages.

I worked on the product flows and the TypeScript service, including role checks, persistent delivery and transfer to another operator. The stack is Node.js, Fastify, PostgreSQL and Docker.

[繁體中文](README.zh-TW.md) · [Architecture](docs/architecture.md) · [Delivery notes](docs/delivery-decisions.md)

## An open menu can outlive its owner's authority

The service checks the current group owner when a sensitive action is applied. Keeping an old settings menu does not preserve management rights after a role change. Ordinary members can still participate without going through the owner's interface.

## Unknown delivery needs its own state

A persistent outbox tracks messages through delivery. Rate limits can be deferred. Known failures can be recorded. If a timeout leaves the outcome uncertain, blindly retrying can send the same message twice, so the item stays visible for review.

Moderation also checks roles and message provenance. A familiar-looking name or button is not enough to identify a trusted service message.

## Moving the service

I included shutdown, backup, restore and ownership reconciliation in the handoff. Platform ownership and application ownership need to agree before the recipient starts the service. The old runtime must stop first.

The private records include automated regressions, API role checks, selected Telegram journeys and transfer-package validation. Recipient operation and the remaining device/language checks are listed in [validation notes](docs/verification.md).

Source and client details are private. This case uses generic names and contains no live bot or customer data. Development was AI-assisted; the bot's product behavior is rule-based. [Disclosure](DISCLOSURE.md)
