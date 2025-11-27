# Ben Ogungbeje – Smart Contract Audit Portfolio

Welcome 👋

This repository showcases a selection of my **smart contract security work**, including:

- Internal audits of production-grade contracts (escrow, multisig, DAO governance)
- Threat models and security notes
- CTF and wargame writeups (Ethernaut, Damn Vulnerable DeFi, Capture the Ether, Guardian Rails)
- Research notes on common EVM vulnerability classes

I have **5+ years of Solidity and EVM experience** and am transitioning my focus fully into **smart contract security research and auditing**, with a strong emphasis on:

- Adversarial thinking
- Exploit reproduction
- Clear, actionable reporting
- Open-ended security research

---

## Highlights

- 🧪 Completed **Damn Vulnerable DeFi**, **Ethernaut**, **Capture the Ether**, **Johnny Time Blockchain Security**, and **Guardian Rails**.
- 🧷 Designed and audited **escrow + multisig + DAO** flows for rent deposit and dispute resolution (CrossRent / UltraRentz).
- 🧬 Attended **DeFi Security Summit 2024**.
- 📰 Read **Rekt News** and **BlockThreat Intelligence** weekly for ongoing exploit analysis.
- 🛠️ Use tools such as **Foundry**, **Hardhat**, **Slither**, **Echidna**, and **Mythril** in my workflow.

---

## Contents

- [`audits/`](./audits)
  - Internal reviews and sample audit reports (escrow, multisig, NFT flows, DAO).
- [`ctf-writeups/`](./ctf-writeups)
  - Selected writeups and notes from real CTFs and security wargames.
- [`research/`](./research)
  - Deeper dives into vulnerability classes and EVM behaviour.

---

## Methodology (High Level)

My typical audit / review process:

1. **Context & Threat Model**
   - Understand protocol goals, trust assumptions, and economic incentives.
   - Identify primary assets at risk and key invariants.

2. **Manual Code Review**
   - Line-by-line reading with attention to:
     - State transitions and invariants
     - Access control and privilege escalation
     - External call patterns
     - Price/oracle assumptions
     - Rounding, precision, and edge cases

3. **Adversarial Reasoning**
   - Attempt to break assumptions:
     - Reentrancy
     - Oracle manipulation
     - Flash loan abuse
     - Governance takeovers
     - Signature replay / permit misuse
     - Storage collision (upgrades / proxies)

4. **Tooling**
   - Static analysis: Slither, Mythril.
   - Fuzzing/invariants: Foundry, Echidna.
   - Differential / scenario testing: Foundry tests and custom scripts.

5. **Reporting**
   - Classify issues by **Severity** and **Likelihood**.
   - Provide:
     - Description
     - Impact
     - Exploit scenario / PoC outline
     - Recommendation
     - Suggested code changes.

> **Note:** This repo only includes **sanitised and non-confidential** material.  
> Real client-specific details are omitted or generalized.

---

## Contact

- **Name:** Ben Ogungbeje  
- **Email:** `ben@ultrarentz.co.site`  
- **GitHub:** [github.com/benpaymaster](https://github.com/benpaymaster)  

If you’d like to see more in-depth, private work, I’m happy to walk through selected code and reasoning in an interview or pairing session.
