# AccordBridge Contracts

**Status: planning and evaluation only.** No AccordBridge smart contract code, deployed instance, audited release, or real-fund integration exists.

This repository owns the financial rules, authority model, escrow-provider evaluation, and future contract verification/deployment evidence for the AccordBridge Stellar platform.

## Intended responsibilities

- Milestone funding and authorized release.
- Disputed settlement, refunds and splits.
- Asset, network, amount and fee validation.
- Protection against unauthorized and duplicate financial actions.
- Test coverage and reproducible deployment/audit records for the exact selected implementation.

Stellar/Soroban is the intended contract platform. If custom contracts are needed, Rust is the anticipated implementation language; no SDK or toolchain has been selected for our product.

## Documents

- [Provider evaluation](docs/PROVIDER-EVALUATION.md)
- [Validation matrix](docs/VALIDATION.md)
- [Canonical product rules](https://github.com/accordbridge-labs/accordbridge-backend/blob/main/docs/PRODUCT.md)

Trustless Work remains a candidate, not an approved production dependency. A separate escrow per milestone is proposed for evaluation. Do not describe timeout release, restricted dispute recipients, or bilateral contract amendments as implemented protections.

No upstream code has been copied into this repository. License and reuse decisions remain pending. See the planning issues for next steps.
