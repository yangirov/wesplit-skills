---
name: wesplit-setup
description: Connect WeSplit via OAuth, verify access to an event and understand its participants and currency.
---

# Set up WeSplit

1. Verify the MCP connection with `wesplit_get_context` and list accessible events using `wesplit_list_events`.
2. For the selected event, call `wesplit_get_event` and verify currency, current participants and rights. Do not infer the user's payer identity from their account name.
3. Ask only for essential missing details when recording a purchase. There are no saved Quick Add defaults, direct-write mode or per-purchase limits.
4. All mutations use `wesplit_prepare_*_change`, user review and `wesplit_commit_change` after approval. For an uncertain result use `wesplit_get_change_status`.
5. Event invitations and participant access are managed through the app's permanent event link; MCP does not manage invitation links.
