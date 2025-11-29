# Reentrancy Patterns & Mitigations

## Classic Pattern

- External call before state update.
- Attacker reenters and drains state based on stale data.

**Mitigation:**

- Checks-Effects-Interactions.
- Reentrancy guards.
- Avoid external calls where not needed.

---

## Cross-Function Reentrancy

- Vulnerability arises when:
  - Function A updates state.
  - Function B assumes that state is stable during an external call.

**Mitigation:**

- Consider global reentrancy assumptions.
- Treat external calls as boundaries where invariants may be broken.

---

## Read-Only Reentrancy

- Protocols that rely on external views (e.g. for pricing) can be manipulated if the external contract sees the system mid-reentry.

**Mitigation:**

- Avoid using intermediate state in external pricing or accounting.
- Prefer oracles or delayed snapshots.
