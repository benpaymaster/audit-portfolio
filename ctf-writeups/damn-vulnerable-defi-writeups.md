# Damn Vulnerable DeFi – Selected Level Notes

These are high-level notes for some Damn Vulnerable DeFi challenges I’ve completed, focusing on *what I learned* rather than full exploit code.

---

## Unstoppable

**Concepts:** Overflow, token invariants, lending assumptions.

**Key Lessons:**

- Lending pools often assume invariants around token balances.
- If a user can break the accounting assumptions (e.g. by sending tokens directly), functions relying on `balanceOf` vs internal accounting can revert or misbehave.
- Protocols should:
  - Use internal accounting or
  - Restrict direct transfers that break invariants.

---

## Naive Receiver

**Concepts:** Misuse of `tx.origin`, fee-on-transfer patterns, external calls.

**Key Lessons:**

- If the lending contract allows anyone to trigger operations on behalf of a user without their consent, the user can be griefed into paying fees.
- Protocols must ensure:
  - The caller is authorised.
  - The user explicitly opts in to actions that incur fees.

---

## Truster

**Concepts:** Arbitrary call abuse, approvals.

**Key Lessons:**

- Allowing arbitrary calls from a pool contract (e.g. `target.functionCall(data)`) can grant attackers approvals or move tokens without direct transfer logic.
- Always constrain:
  - Which contracts can be called.
  - Which functions can be executed.
  - The parameters used.

---

## Side Entrance

**Concepts:** Reentrancy, deposit vs borrow confusion.

**Key Lessons:**

- Treat deposit and loan accounting separately.
- If a borrower can reenter during execution and make the pool “believe” the loan was repaid through an internal balance, funds can be stolen.
- Use reentrancy guards and make accounting explicit.

---

## Takeaways

Damn Vulnerable DeFi sharpened my intuition for:

- How fragile economic assumptions can be.
- Why “innocent” helper functions or arbitrary calls can become critical attack vectors.
- The importance of testing weird edge cases and not just the happy path.
