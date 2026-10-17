---
name: wesplit-add-expense
description: Record one explicitly requested expense in a named WeSplit event or saved default.
---

# Record an expense

1. Resolve the intended event. If the user names one, use `wesplit_list_events` to find it and `wesplit_get_event` to verify exact ownerUid/eventId, currency, participants and payment methods. Do not overwrite saved preferences. If no event is specified, use authorized `wesplit_get_preferences` defaults. Ask when missing or ambiguous.
2. Explicit user details take precedence over saved preferences, which apply only to their matching event. Verify the payer and split members. Never silently borrow a payer or participants from another event.
3. Resolve payment methods by their verified ID. For individual shares pass `allocations` and matching `members`, with exact amounts adding up to the purchase total. If no allocation is specified, use equal split.
4. Call `wesplit_create_purchase` directly with `ownerUid` and `eventId` for an explicit event, exact date, amount, optional `paymentMethodId` and `allocations`, and a stable unique `requestId`. No enable switch, spending cap or extra prepare/commit. Host approvals still apply.
5. After uncertain responses retry only the same ID and identical payload. Report success only after server confirmation.
