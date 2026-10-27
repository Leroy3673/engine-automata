# Engine Automata

**An intelligent identity consistency engine for multimodal verification, state-machine-driven workflows, and Ethereum smart-contract integration.**

## Overview

Engine Automata is an experimental intelligent systems engineering project exploring how multimodal AI, explicit state machines, and blockchain-based authorization can work together to evaluate identity consistency and protect sensitive operations.

The engine is designed to evaluate visual and authentication evidence, manage verification workflows through defined state transitions, and produce cryptographically verifiable authorization attestations that Ethereum smart contracts can validate.

The project is not limited to decentralized finance (DeFi). Ethereum contracts serve as an execution and verification environment for testing the engine across different applications and authorization scenarios.

## Objectives

- Develop an identity consistency engine capable of evaluating visual and authentication evidence.
- Model verification workflows as explicit, testable state machines.
- Separate evidence processing, verification decisions, attestation issuance, and on-chain authorization.
- Integrate Rust-based verification services with Solidity smart contracts and TypeScript applications.
- Explore multimodal AI techniques for visual identity consistency and authentication.
- Establish secure interfaces between off-chain intelligence and on-chain execution.
- Evaluate reliability, privacy, replay protection, authorization scope, and failure handling.

## Core Architecture

The project is organised around three complementary engineering layers.

### 1. Intelligent Verification

**Primary language: Rust**

Responsible for verification workflow orchestration, evidence processing, consistency evaluation, session management, policy enforcement, and authorization attestation generation.

Multimodal AI components will support visual evidence analysis. Their outputs will be treated as uncertain evidence rather than unquestionable proof of identity.

### 2. Ethereum Integration

**Primary language: Solidity**

Responsible for verifying cryptographic attestations and enforcing application-specific authorization rules.

Smart contracts may validate issuer authorization, expiry, nonces, action scope, and revocation status. The contracts will not process raw biometric evidence or rely on AI-generated decisions without an explicit verification and trust model.

### 3. Application and Wallet Integration

**Primary language: TypeScript**

Responsible for the user interface, evidence-submission workflow, wallet connectivity, interaction with Rust services, and communication with Ethereum contracts.

## State-Machine Architecture

Engine Automata follows a state-machine-oriented design in which each machine has a defined responsibility, state, transition rules, and invariants.

The initial conceptual machines are:

- **Verification Session:** manages evidence collection, evaluation, retries, review, rejection, and expiry.
- **Authorization Attestation:** manages issuance, validity, consumption, and revocation.
- **Protected Action:** manages authorization checks and execution within an Ethereum application.

These machines interact through explicit interfaces rather than sharing unrestricted internal state.

The objective is to make verification workflows observable, reproducible, independently testable, and resistant to invalid state transitions.

## Intended Technology Stack

| Technology | Responsibility |
|---|---|
| Rust | Verification engine, state management, backend services |
| Solidity | Ethereum authorization and smart-contract enforcement |
| TypeScript | Application interface, wallet and contract integration |
| Multimodal AI | Visual evidence analysis and identity consistency assessment |
| Ethereum | Execution and validation environment |
| Foundry | Smart-contract testing and development, if adopted |

Specific models, libraries, and infrastructure will be selected and documented as the implementation develops.

## Initial Development Scope

The minimum viable prototype will focus on one complete verification-to-authorization workflow:

1. Establish a synthetic identity reference and a verification session.
2. Submit visual evidence for consistency assessment.
3. Evaluate the result through explicit verification policies and state transitions.
4. Issue a signed, time-limited authorization attestation when the policy requirements are satisfied.
5. Submit the attestation to an Ethereum test contract.
6. Allow or reject a protected action according to the contract's authorization rules.

The first Ethereum demonstration will use test accounts and non-production assets.

## Security and Privacy Principles

- Raw identity documents, images, and biometric templates remain off-chain.
- Verification results are not treated as absolute proof of identity.
- Uncertain or inconclusive evidence must not automatically result in authorization.
- Attestations must be bound to their intended wallet, chain, contract, action, and validity period.
- Expired, unauthorized, revoked, or replayed attestations must be rejected.
- Smart contracts must enforce authorization independently of the client interface.
- Signing keys, sensitive evidence, and verification records must be protected appropriately.
- The system must support testing of failure cases as well as successful verification.

## Project Status

**Status: Architecture and initial specification**

The repository currently establishes the project foundation. The architecture, state machines, interfaces, technology choices, and security requirements will be refined before implementation.

## Development Roadmap

- [ ] Define system boundaries and component responsibilities.
- [ ] Specify verification-session state machines and transition invariants.
- [ ] Define the authorization-attestation schema.
- [ ] Establish the Rust service interfaces.
- [ ] Implement and test the initial Solidity authorization gate.
- [ ] Integrate visual consistency evaluation.
- [ ] Build the TypeScript application and wallet workflow.
- [ ] Demonstrate end-to-end verification and authorization on a test network.
- [ ] Document evaluation results, limitations, and security assumptions.

## Disclaimer

Engine Automata is an experimental engineering project. It is not a production-ready identity verification service, a guarantee of identity authenticity, or a security audit of any Ethereum protocol. Verification accuracy, privacy, and security properties must be evaluated before deployment in real-world applications.

## License

To be determined.
