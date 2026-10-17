---
name: wesplit-batch-expenses
description: Record multiple explicitly requested purchases in one named or default WeSplit event.
---

# Batch expenses

- Resolve the named event through `wesplit_list_events` and `wesplit_get_event`, or use `wesplit_get_preferences` when no event is specified. Never change saved preferences just to record a purchase.
- Verify exact payer, participants, currency and payment methods for that event. Apply explicit user instructions first; saved defaults apply only to their matching event.
- Parse each title, amount, date, payer, split, optional `allocations` and `paymentMethodId`. Validate that allocations sum to each purchase total.
- Call `wesplit_create_purchases_batch` with `ownerUid`/`eventId` for an explicit event, one stable `batchId`, and the ordered items with exact dates. No spending cap or enable switch.
- Preserve the batchId and identical payload on retries. Inspect each result, disclose partial successes and do not claim atomicity. Respect host approvals.
