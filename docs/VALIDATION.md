# Required validation — not executed for AccordBridge

| Scenario | Expected evidence |
| --- | --- |
| Agreement changes between review and funding | Funding rejects stale expected terms |
| Wrong network, asset or amount | Action is rejected or clearly held pending correction |
| Insufficient/partial deposit | Work is not shown as fully funded |
| Happy-path approval and release | Exact gross/fee/net amounts reconcile with chain state |
| Unauthorized release or resolution | Contract rejects signatures without the required authority |
| Duplicate release/retry | No second payout; prior result can be recovered |
| Client silence | Documented escalation works; no invented timeout permission |
| Revision versus extra scope | Records preserve scope; extras require acceptance and new funding |
| Refund or split | Correct authorized recipients and fee treatment; no unexplained residual funds |
| Dispute concurrent with payout | Only a valid financial outcome can commit |
| Resolver unavailable/conflicted | Agreed recovery or replacement process is technically possible |
| Indexer/API unavailable | Chain reconciliation restores state without duplicate payment |
| Contract storage archival | Restoration and lifetime maintenance are demonstrated |
| Excess/accidental deposits | A defined authorized recovery path and fees are documented |
| Wallet key loss | Limitations and any recovery authority are explicitly documented |

## Evidence record

For each run record network, contract ID, executable hash, source revision, dependency/tool versions, transaction hashes, expected and actual balances, and relevant audit scope. Separate mocked host tests, real-signature tests, testnet transactions, and mainnet evidence.

No mainnet execution is part of organization setup. An independently reviewed implementation and functioning operating procedures are prerequisites for a real-money pilot.
