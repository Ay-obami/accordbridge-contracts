# Escrow-provider evaluation — 2026-10-08

## Recommendation

Trustless Work is provisional. Continue specification and prototype work, but do not declare the integration ready for real funds.

## Evidence inspected

- V1 single-release source: [`6e4d40e25057dc51fcffd9c5cbee05eaf369380a`](https://github.com/Trustless-Work/trustlesswork-smart-contract-stellar/tree/6e4d40e25057dc51fcffd9c5cbee05eaf369380a).
- V1 multi-release source: [`d5cfc2ee0341141ab0a348388771afe71c8c28d2`](https://github.com/Trustless-Work/trustlesswork-smart-contract-stellar/tree/d5cfc2ee0341141ab0a348388771afe71c8c28d2).
- V2 multi-release development source: [`ab06d9c60fa5560b0bc17cf8fb77d89ffeb2fcbd`](https://github.com/Trustless-Work/trustlesswork-smart-contract-stellar/tree/ab06d9c60fa5560b0bc17cf8fb77d89ffeb2fcbd).
- [Runtime Verification audit delivered November 7, 2025](https://www.trustlesswork.com/20251107%20Trustless%20Work%20Audit%20Report.pdf).
- [V2 September 22, 2026 announcement](https://www.trustlesswork.com/escrow-times/news-v2-testnet): V2 testnet-only, external audit incomplete; V1 remains the provider's production offering.
- [Provider pricing](https://www.trustlesswork.com/pricing): advertised 0.3% protocol release fee plus optional integrator fee.

## What the source review established

Basic deposits, approved releases, milestone disputes and resolver-directed distributions exist. The inspected release logic requires approval and an authorized signer; no seven-day timeout entitlement was established. Multi-release deposits enter a common balance, without individually reserving each deposit for a particular milestone.

Permitted escrow changes are controlled by designated roles, not necessarily by both commercial parties signing. Refund/dispute distribution code applies fees. Resolver distribution maps are not restricted solely to the original client and freelancer by the inspected recipient checks. These are authority and product-fit observations, not a comprehensive security audit.

## Local verification result

On a temporary copy of the exact V1 single-release revision, Rust 1.91.0 ran `cargo test --workspace --locked` successfully, but **zero tests executed** because `src/lib.rs` comments out the test module. Temporarily enabling only that module produced **12 E0061 compilation errors** from outdated test call signatures. The temporary change was reverted. V1 multi-release source also has its test module commented out; it was inspected but not executed locally.

This does not establish a deployed exploit or prove the production code is unsafe. It means the inspected revision does not supply a runnable, meaningful suite through the normal test command. Existing test helpers also mock authorization; passing such tests alone would not verify real signing behaviour.

## Unresolved evidence

- No complete production contract → executable hash → source revision → applicable audit mapping was established.
- The published audit is version-scoped and recommends further review after substantial remediation. It is not blanket coverage of later branches or our integration.
- The V1 API specification was accessible, but an unauthenticated testnet escrow lookup returned HTTP 401. No provider API credential was created or supplied.
- No authenticated end-to-end testnet flow or mainnet transaction was performed. Self-deploying source would validate that copy, not identify the provider's hosted production version.

## Exit criteria

Obtain exact-version deployment/audit evidence; demonstrate meaningful current tests; verify provider integration on testnet; document refund economics, resolver powers, consent rules, availability/recovery and per-milestone funding. Evaluate a separate audited implementation or custom work only through an explicit technical decision.
