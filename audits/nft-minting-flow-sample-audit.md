# NFT Minting Flow – Sample Security Review (Sanitised)

**Author:** Ben Ogungbeje  
**Status:** Sample / Educational  

> This is a sample-style review based on typical NFT minting contracts and flows I’ve worked with. It demonstrates how I structure findings and reasoning, with all project-specific details removed.

---

## 1. Scope

The review focuses on:

- Public and whitelist mint functions
- Supply limits and per-wallet limits
- Payment logic and withdrawal
- Metadata and URI management
- Role-based access control (admin, minter roles)

Out of scope:

- Frontend & marketplace integrations
- Off-chain whitelist generation

---

## 2. Methodology

- Manual review of Solidity contracts.
- Use of **Slither** for common patterns:
  - Reentrancy
  - Incorrect `onlyOwner` / access control
  - Dangerous `tx.origin` usage
- Scenario-based tests:
  - Multiple mints per wallet
  - Max supply edge conditions
  - Paused/unpaused state behaviour

---

## 3. Key Invariants

- Total minted supply must never exceed `maxSupply`.
- A single wallet must not exceed `maxPerWallet` across all mints.
- Minting must revert if contract is paused.
- ETH payments must match the configured mint price.
- Withdrawals must go only to the designated payout address.

---

## 4. Findings (Sample)

### 4.1 Medium – Missing `maxPerWallet` Enforcement on Whitelist Mint

**Description**  
The whitelist mint function checked global supply but did not enforce `maxPerWallet`. A whitelisted address could mint repeatedly by splitting calls.

**Impact**  
A single address could accumulate more NFTs than intended, skewing distribution and potentially impacting fair launch dynamics and market trust.

**Recommendation**  

- Track mints per address in both public and whitelist mint paths.
- Use a shared internal function that applies the same invariant checks for all mint entrypoints.

---

### 4.2 Medium – Unrestricted `setBaseURI`

**Description**  
`setBaseURI()` was callable by any address due to a missing `onlyOwner` / role check.

**Impact**  
An attacker could change the metadata to malicious or offensive content, damaging brand reputation and trust.

**Recommendation**  

- Restrict `setBaseURI` to a well-defined admin role.
- Consider using `AccessControl` with explicit `URI_ADMIN_ROLE`.

---

### 4.3 Low – Event Gaps on Critical State Changes

**Description**  
Changing mint price or pausing/unpausing the contract did not emit events.

**Impact**  
Off-chain systems (frontends, indexers, alert systems) would have to poll rather than subscribe to changes, which can lead to UX issues.

**Recommendation**  

- Emit events for:
  - `MintPriceUpdated`
  - `Paused` / `Unpaused`
  - `BaseURIUpdated`

---

## 5. Summary

The NFT minting flow is generally sound after fixing:

- Per-wallet limits across all mint paths
- Admin-only URI management
- Better event coverage

Future improvements include:

- Optional royalty configuration using standard interfaces
- More granular admin roles
- Stronger separation between operational roles and payout wallets.
