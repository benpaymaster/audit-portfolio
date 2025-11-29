# Oracle Manipulation & Price Attacks

## Direct LP Manipulation

- Attackers can move pool prices by:
  - Large swaps
  - Flash loans
- Protocols that read TWAP or spot prices directly from AMMs within the same tx are vulnerable.

**Mitigation:**

- Use TWAP with sufficient window.
- Use multiple sources.
- Cap price impact per block/tx.

---

## Off-Chain Oracles

- Centralized oracles can be:
  - Delayed
  - Censored
  - Spoofed.

**Mitigation:**

- Decentralised oracle networks.
- Validations and sanity checks.
