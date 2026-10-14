---
name: wesplit-settlements
description: Explain debts between participants or record a reviewed repayment in WeSplit.
---

# Balance and repayments

- Use `wesplit_get_balance` for confirmed balances; identify exactly who owes whom, currency and net position.
- Distinguish recording a repayment in WeSplit from sending money externally: this plugin does not transfer funds.
- To record repayment use `wesplit_prepare_repayment_change`, display debtor, creditor, amount and affected event, obtain explicit required approval, then call `wesplit_commit_change`.
- Never infer that a debt was repaid merely from casual wording. Never bypass scope or safety confirmations.
- If commit outcome is uncertain, use `wesplit_get_change_status` and do not prepare a replacement.
