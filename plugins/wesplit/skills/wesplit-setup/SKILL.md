---
name: wesplit-setup
description: Configure saved WeSplit event, payer, split members and IANA timezone for fast agent expense entry.
---

# Configure WeSplit

1. Call `wesplit_list_events` and `wesplit_get_event` to verify event, members, currency and rights.
2. Ask only for missing event or exact payer identity. Let the user choose split members; otherwise default to all event members.
3. With explicit authorization, call `wesplit_set_preferences` to save event, payer, split and timezone.
4. Direct expense tools require write access, not an enable switch or monetary limit. Never request either.
5. Other mutations, including deletions and repayments, retain prepare/review/commit and required approvals.
6. Confirm saved event, payer, split, timezone and currency.
