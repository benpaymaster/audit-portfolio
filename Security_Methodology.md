# Security Review Methodology

This document outlines my personal methodology when performing smart contract audits and vulnerability research.

---

## 1. Threat Modelling

Before reading code, I identify:

- Primary assets at risk  
- Critical invariants (e.g., "escrow funds cannot be released early")  
- Trust assumptions  
- External dependencies  
- Oracle assumptions  
- Privileged roles and attack surface  

This establishes the lens through which I review code.

---

## 2. Manual Code Review (Line-by-Line)

Primary focus areas:

- State transitions and invariants  
- External call boundaries  
- Untrusted inputs  
- Reentrancy triggers  
- Price / oracle assumptions  
- Signature validation  
- Storage layout and upgrade safety  

I annotate code and track all state-changing functions.

---

## 3. Adversarial Analysis

I attempt to break:

- Balance accounting  
- Privilege boundaries  
- Invariant assumptions  
- Deadline / nonce logic  
- Fee calculations  
- Flash loan resistance  

This includes simulating:

- Reentrancy  
- Oracle manipulation  
- Replay attacks  
- Governance attacks  
- Cross-function interactions  

---

## 4. Static Analysis

Tools:

- **Slither** for code smells & common patterns  
- **Mythril** for symbolic execution  
- **Surya** for contract architecture graphing  
- **Slither-check-upgradeability** where relevant  

---

## 5. Fuzzing & Invariants

Using Foundry/Echidna, I test:

- State machine invariants  
- Economic constraints  
- Signature validity  
- Overflow/underflow edge cases (when using unchecked blocks)  

---

## 6. Reporting

Each finding includes:

- **Title**  
- **Severity** (Critical, High, Medium, Low, Info)  
- **Affected code snippet**  
- **Attack scenario**  
- **Proof of concept (if appropriate)**  
- **Impact explanation**  
- **Recommended remediation**  
- **Post-fix verification notes**  

Clear communication is essential.

---

## 7. Continuous Learning

I stay current by:

- Solving security wargames  
- Studying DeFi hack post-mortems  
- Reading weekly **Rekt News** & **BlockThreat Intelligence**  
- Attending security summits & conferences  
- Monitoring GitHub issues and patches for major protocols  

My goal is to maintain an attacker mindset at all times.

---

This methodology aligns closely with industry-leading practices used by  
OpenZeppelin, Trail of Bits, ChainSecurity, & Spearbit researchers.
