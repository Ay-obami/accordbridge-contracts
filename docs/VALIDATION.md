# Validation status — experimental testnet

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

## Executed for this experiment

- Seven Rust host tests (five escrow, two token): both approvals and exact funding/release; duplicate fund/release rejected; mutual refund restricted to original participants/recipient; missing authorization without mocks; wrong terms and insufficient funds; wrong network rejected. Token tests also cover the faucet, transfer balance conservation, self-transfer, negative/insufficient amounts, missing authorization and network restriction. Most state tests use mocked authorization; they are not real-signature evidence.
- Real-signature testnet smoke: [deployment](../deployments/testnet.json) and [escrow run](../deployments/smoke-testnet.json) record pinned hashes, participants, amount and transaction hashes. Funding and release states were queried from chain. An outsider-signed release failed before the authorized release.
- Backend testnet run: sibling `docs/evidence/testnet-api.json` records wallet-proof linkage, deployment, both on-chain approvals, funding with verified escrow balance, first refund vote retaining funded state, and second vote returning funds with zero held balance.
- Backend isolated-database tests cover tampered/wrong-wallet/wrong-network proof signatures, replay, role restrictions, frozen terms, same prepared intent reuse, unknown submission and retained-history expiry.

The table above remains the wider production acceptance checklist. Disputes/resolvers, client-silence escalation, change-order funding, accidental deposits, storage archival and key recovery are **not implemented or validated**. Fee logic is zero for this experiment. Automated browser tests cannot substitute for manual Freighter extension review. No audit or mainnet evidence exists.

Build input file digests and toolchain versions are recorded in [build-inputs.json](../deployments/build-inputs.json). Backend reconciliation also rejects cross-ledger state/balance snapshots and snapshots older than transaction confirmation.
