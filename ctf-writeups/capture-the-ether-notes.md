# Capture the Ether – Notes

Capture the Ether helped me practice low-level EVM and Solidity quirks.

---

## Token Sale

**Lesson:** Integer overflow in price calculations.

- Multiplying `msg.value * price` can overflow and create unrealistic token balances.
- Use `unchecked` intentionally and very carefully, or rely on SafeMath patterns in legacy contexts.

---

## Nickname / Account Takeover Challenges

**Lesson:** Understanding how storage slots and variables map to state.

- By manipulating storage directly or exploiting bad access control, you can overwrite ownership.
- Highlighted the importance of:
  - Explicit ownership patterns.
  - Avoiding magic constants.
  - Careful initialisation.

---

## Randomness Challenges

**Lesson:** On-chain “randomness” is usually predictable.

- Using `block.timestamp`, `blockhash`, or similar as a randomness source can be gamed by miners or attackers.
- True randomness typically requires:
  - Off-chain oracles (e.g., Chainlink VRF).
  - Commit-reveal schemes.
