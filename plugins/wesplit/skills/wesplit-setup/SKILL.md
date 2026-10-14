---
name: wesplit-setup
description: Configure WeSplit default event, verified payer, split members, IANA timezone and optional safely capped Quick Add.
---

# Configure WeSplit

When the user wants fewer questions or requests default settings:

1. Call `wesplit_list_events` and identify an accessible event; fetch `wesplit_get_event` for its exact members, currency and rights.
2. Ask for any missing event or exact payer identity. Suggest splitting between all event members unless the user chooses a subset.
3. Call `wesplit_set_preferences` when user explicitly authorizes saving settings.
4. Quick Add is OFF by default. Explain that enabling it authorizes direct purchases within the selected event and maximum amount per purchase; it does not disable host approvals.
5. Never enable Quick Add or set a spending limit without explicit consent. Clarify that repay/delete/access changes still need approval.
6. Confirm saved event, payer, split, timezone, currency and mode succinctly.
