# Delivery decisions for a TPM discussion

This page connects the existing anonymized bot case to authority, dependencies, acceptance, and transfer. It does not publish customer records or add a claim of recipient operation.

## Define the interaction and authority boundary

Members participate in their group. The current group owner manages sensitive actions in private. Platform bot ownership, application ownership, group ownership, and the runtime each have a separate role in making a transfer usable.

## Decisions and their consequences

| Decision | Consequence for the delivery | Acceptance question |
| --- | --- | --- |
| Recheck current group ownership | A menu cannot permanently carry authority from an earlier role. | Does a stale action fail after ownership changes? |
| Keep member participation in the group | Private management changes must not break ordinary-member flows. | Can a member complete participation without entering an owner workflow? |
| Persist delivery intent and outcomes | Queued, sent, failed, deferred, and unknown cannot be interchangeable. | What happens after a timeout when delivery may already have occurred? |
| Distinguish message provenance from appearance | Moderation depends on trusted event information and permissions. | Can a copied name or button be mistaken for a trusted service message? |
| Stop the old runtime before transfer | Service ownership and active processing must be reconciled. | Does the recipient start only the intended runtime with compatible state? |

## Dependency and responsibility map

| Boundary | Dependency | Acceptance responsibility |
| --- | --- | --- |
| Telegram role ↔ management action | Current role lookup and recoverable lookup failure. | Group owner plus implementer. |
| Bot permissions ↔ moderation | The required permissions and delivered event coverage. | Group owner and bot operator. |
| Outbox ↔ external send | Durable intent, delivery outcome, and a review path. | Operator handling failures and uncertain results. |
| Source runtime ↔ recipient runtime | Backup, restore, compatible decryption material, and aligned ownership. | Source and recipient operators through private channels. |

These categories express system responsibilities; they do not imply a particular team size or named customer's organization.

## Verification and handoff

The [verification summary](verification.md) keeps automated checks, API authority checks, selected Telegram client journeys, and transfer validation separate. Later changes that lack a fresh client walkthrough remain gaps. Recipient-machine, role, device, language, payment, and hosting acceptance cannot be inferred from a prepared archive.

A technical discussion can follow one failure through the affected roles, state changes, recovery, and the evidence needed to close it. No leadership, schedule, capacity, or business-result claim is added by this page.
