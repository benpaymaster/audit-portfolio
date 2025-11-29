# EVM Storage Layout & Upgrade Risks

**Focus:** How storage layout works in Solidity and how it can be broken in upgradable contracts.

## Slots & Packing

- State variables are stored in 32-byte slots.
- Values may be packed when size < 32 bytes.
- Misalignment in upgraded contracts can overwrite critical variables (e.g. owner, balances).

## Vulnerability Class

- Adding variables before existing ones.
- Changing types or order across versions.
- Using `delegatecall` with mismatched layouts.

## Mitigations

- Use well-audited upgrade patterns (e.g. OZ’s UUPS / Transparent Proxy).
- Avoid manual slot juggling where possible.
- Use storage gap patterns.
- Include tests that check invariants across upgrades.

