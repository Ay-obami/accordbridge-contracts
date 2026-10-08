# Decision: isolated testnet experiment

The provider evaluation has unresolved credentials, deployed-code/audit mapping and authority questions. Instead of representing those as solved, this experiment uses a small custom escrow to validate wallet proofs, frozen agreements, signed transactions, and reconciliation. It does not select or approve a production provider.

The immutable state binds client, freelancer, asset, amount and agreement hash. Both participants approve before client funding. Release requires client authorization and pays only the freelancer. A full refund needs both votes and pays only the client. Contract state and token transfers commit atomically; repeated payout transitions fail. No operator, resolver or upgrade entry point exists. Refund votes persist and cannot be withdrawn; the client may still release after one refund vote. This is not dispute handling.

ABUSD is a narrow development token with a public faucet and no financial value. It is not USDC and does not implement the complete SEP-41 surface. The application uses nominal agreement numbers only to exercise seven-decimal token accounting. Do not fund this implementation with valuable assets.

Instance and touched token balance lifetimes are extended on writes, but long-term lifetime maintenance, archival restoration, testnet resets and recovery are not handled. An accidental/excess deposit has no sweep path; payout moves only the immutable amount. Key loss can leave tokens locked. There is no emergency administrator or timeout escape. These are explicit experimental limitations.

The checked-in deployment pins executable hashes; Cargo.lock and rust-toolchain.toml pin the build inputs. Public testnet transaction artifacts establish the runs described in VALIDATION.md, not an audit or production guarantee. Any future contract change needs a new build/hash, deployment and validation rather than silently reusing this evidence.
