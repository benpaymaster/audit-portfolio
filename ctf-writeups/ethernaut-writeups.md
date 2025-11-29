# Multisig + DAO Dispute System – Threat Model (Sanitised)

**Author:** Ben Ogungbeje  

## 1. Assets

- Escrowed rent deposits.
- DAO voting power and decisions.
- Signer private keys (tenant/landlord reps).
- Reputation / system trust.

## 2. Adversaries

- Malicious tenant or landlord.
- Colluding signers (subset of the 6).
- Compromised DAO governance (whale, governance attack).
- Off-chain integration bugs.

## 3. Key Threats

- **T1 – Unauthorised release of funds** via:
  - Multisig replay attacks.
  - DAO payload manipulation.
- **T2 – Permanent lock of funds** by:
  - Deadlocked multisig.
  - Dispute states with no escape hatch.
- **T3 – State desynchronisation** between:
  - DAO recorded decisions and contract state.
- **T4 – Governance capture**:
  - A hostile DAO controlling resolution outcomes.

## 4. Controls

- Nonce + deadline for approvals.
- Strict parameter validation in the execution function.
- Explicit allowed action types for DAO resolutions.
- Emergency admin / safety module with limited, transparent capabilities (e.g. only to unlock frozen state with DAO oversight).

## 5. Residual Risk

- Social engineering and off-chain governance risks remain.
- Mitigation: clear documentation and DAO process design.

This doc represents an example of how I structure **threat modelling** around multisig + DAO flows.
