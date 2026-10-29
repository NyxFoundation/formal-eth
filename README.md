# Awesome Ethereum Formal Verification [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome Ethereum formal verification tools, projects, and resources

Formal verification is a mathematical approach to proving the correctness of smart contracts and blockchain protocols. This list focuses on formally verified Ethereum-related projects, tools, and academic research.

## Contents

- [Awesome Ethereum Formal Verification ](#awesome-ethereum-formal-verification-)
  - [Contents](#contents)
  - [Projects](#projects)
    - [Cryptography](#cryptography)
    - [Protocol](#protocol)
    - [Application](#application)
  - [Formal Specifications \& Semantics](#formal-specifications--semantics)
  - [Formal Verification Tools](#formal-verification-tools)
    - [Production-Ready Tools](#production-ready-tools)
    - [Emerging Tools](#emerging-tools)
    - [ZK Circuit Verification](#zk-circuit-verification)
    - [Proof Libraries](#proof-libraries)
    - [Archived Tools](#archived-tools)
  - [Security Reports](#security-reports)
    - [Audit Portfolios](#audit-portfolios)
  - [Academic Research](#academic-research)
    - [Research Projects](#research-projects)
    - [Academic Papers](#academic-papers)
  - [Vulnerability Detection](#vulnerability-detection)
    - [Specific Vulnerability Research](#specific-vulnerability-research)
  - [Contributing](#contributing)
    - [Guidelines](#guidelines)
    - [How to Contribute](#how-to-contribute)
  - [License](#license)

## Projects

### Cryptography

| Name                    | Category                 | Formal Verification                                                                                                                                           | Stack        |
| ----------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| KZG Commitment          | Commitment Scheme        | [✅](https://github.com/tobias-rothmann/Polynomial-Commitment-Schemes)                                                                                        | Isabelle/HOL |
| Merkle Tree             | Commitment Scheme        | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib)                                                                                                            | Lean         |
| Binius                  | Commitment Scheme        | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/Binius) (ring-switching + Binary Basefold proved; FRI-Binius in progress)      | Lean         |
| Sumcheck                | Interactive Oracle Proof | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/Sumcheck) (full-protocol soundness landed; knowledge-soundness bridge pending) | Lean         |
| FRI                     | Interactive Oracle Proof | [✅](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/Fri), [✅](https://github.com/banr1/tailored-simple-rbr-fri) (RBR soundness)       | Lean         |
| Batched FRI             | Interactive Oracle Proof | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/BatchedFri)                                                                    | Lean         |
| STIR                    | Interactive Oracle Proof | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/Stir)                                                                          | Lean         |
| WHIR                    | Interactive Oracle Proof | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib)                                                                                                            | Lean         |
| Spartan                 | Interactive Oracle Proof | [🏗️ WIP](https://github.com/Verified-zkEVM/ArkLib/tree/main/ArkLib/ProofSystem/Spartan)                                                                       | Lean         |
| XMSS (leanSig)          | Signature Scheme         | [✅](https://github.com/leanEthereum/leanVM/tree/main/formal/lean_xmss) (SUF-CMA in the ROM)                                                                  | Lean         |
| SPHINCS+ (leanSPHINCS)  | Signature Scheme         | [✅](https://github.com/leanEthereum/leanVM/tree/main/formal/lean_sphincs) (SUF-CMA in the ROM)                                                               | Lean         |
| Poseidon2 (Plonky3 AIR) | Hash Function            | [✅](https://github.com/NethermindEth/poseidon2-fv) (constraint soundness)                                                                                    | Lean         |
| Keccak (Plonky3 AIR)    | Hash Function            | [✅](https://formal.land/blog/2026/01/14/formal-verification-keccak-plonky3) (determinism and correctness)                                                    | Rocq         |
| Keccak / SHA-2 (OpenVM) | Hash Function            | [✅](https://github.com/openvm-org/openvm-fv) (chip soundness)                                                                                                | Lean         |

### Protocol

| Name                                                                  | Category        | Formal Verification                                                                                                                                                                                                                          | Stack                       |
| --------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| Ethereum PoS                                                          | L1              | [✅](https://github.com/runtimeverification/beacon-chain-verification), [✅](https://github.com/Consensys-inc-archive/eth2.0-dafny) (archived)                                                                                               | Rocq, Dafny                 |
| Casper FFG                                                            | L1              | [✅](https://github.com/runtimeverification/casper-proofs)                                                                                                                                                                                   | Rocq                        |
| Gasper                                                                | L1              | [✅](https://github.com/czhang-fm/Gasper-TLA-) (bounded model checking)                                                                                                                                                                      | TLA+, Apalache              |
| 3-Slot Finality (3SF)                                                 | L1              | [✅](https://github.com/freespek/ssf-mc) (Accountable Safety, bounded model checking)                                                                                                                                                        | TLA+, Apalache, CVC5, Alloy |
| RANDAO                                                                | L1              | [✅](https://github.com/runtimeverification/rdao-smc)                                                                                                                                                                                        | Maude, PVeStA               |
| Staking deposit contract                                              | L1              | [✅](https://github.com/runtimeverification/deposit-contract-verification)                                                                                                                                                                   | K Framework                 |
| Consensus specs (Fulu, Gloas, Heze)                                   | L1              | [🏗️ WIP](https://github.com/etheorem/etheorem)                                                                                                                                                                                               | Lean                        |
| [leanSpec](https://github.com/leanEthereum/leanSpec) (Lean Consensus) | L1              | [🏗️ WIP](https://github.com/NyxFoundation/formal-leanSpec), [🏗️ WIP](https://github.com/NyxFoundation/verity) (Verity client)                                                                                                                | Lean                        |
| [EIP1559](https://eips.ethereum.org/EIPS/eip-1559)                    | EIP             | [✅](https://ieeexplore.ieee.org/document/9842730)                                                                                                                                                                                           | UPPAAL                      |
| [Cairo (language)](https://github.com/starkware-libs/cairo-lang)      | zkVM (language) | [✅](https://github.com/starkware-libs/formal-proofs)                                                                                                                                                                                        | Lean                        |
| [leanVM](https://github.com/leanEthereum/leanVM)                      | zkVM            | [🏗️ WIP](https://github.com/leanEthereum/leanVM/tree/FV/formal/lean_vm) (verifier knowledge soundness on the `FV` branch)                                                                                                                    | Lean                        |
| [Jolt](https://github.com/a16z/jolt)                                  | zkVM            | [🏗️ WIP](https://github.com/LayerZero-Labs/jolt-qed) (bytecode expansion proved), [🏗️ WIP](https://github.com/GaloisInc/zkLean)                                                                                                              | Lean                        |
| [SP1](https://github.com/succinctlabs/sp1)                            | zkVM            | [✅](https://github.com/succinctlabs/sp1-lean) (RV64 core chips), [✅](https://medium.com/veridise/verifying-sp1-circuit-determinism-with-picus-a-collaboration-between-veridise-and-succinct-985c7a6dd9b5) (determinism)                    | Lean, Picus                 |
| [OpenVM](https://github.com/openvm-org/openvm)                        | zkVM            | [✅](https://github.com/openvm-org/openvm-fv) (RV32IM chips)                                                                                                                                                                                 | Lean                        |
| [Pico](https://github.com/brevis-network/pico)                        | zkVM            | [✅](https://github.com/NethermindEth/pico-fv) (RV32IM / RV64IM chips)                                                                                                                                                                       | Lean                        |
| [RISC Zero](https://github.com/risc0/risc0)                           | zkVM            | [🏗️ WIP](https://veridise.com/blog/audit-insights/risc-zeros-zk-vm-security-how-veridise-enabled-risc-zero-to-achieve-provable-continuous-zk-security/) (determinism), [🏗️ WIP](https://github.com/NethermindEth/risczero-fv) (archived PoC) | Zirgen, Lean, Picus         |
| [Intmax2](https://github.com/InternetMaximalism/intmax2)              | Zk Rollup       | [✅](https://github.com/NethermindEth/FVIntmax)                                                                                                                                                                                              | Lean                        |
| CBC Casper                                                            | (L1)            | [✅](https://github.com/LayerXcom/cbc-casper-proof)                                                                                                                                                                                          | Isabelle/HOL                |

### Application

| Name                                                     | Category   | Formal Verification                                                                                                    | Stack                          |
| -------------------------------------------------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| [Uniswap V3](https://github.com/Uniswap/v3-core)         | DEX        | ✅                                                                                                                     | Isabelle/HOL based custom tool |
| [Uniswap V4](https://github.com/Uniswap/v4-core)         | DEX        | [✅](https://certora.cdn.prismic.io/certora/Z4UNepbqstJ99YI5_InformedeSeguridadUniswapV4.pdf)                          | Certora Prover                 |
| Compound V3                                              | Lending    | [✅](https://certora.cdn.prismic.io/certora/e7ca6508-fad8-4a41-8588-b3312d8b750e_Compound+Report.pdf)                  | Certora Prover                 |
| Euler Finance V2                                         | Lending    | [✅](https://github.com/euler-xyz/fee-flow/tree/main/formal-verification)                                              | Certora Prover                 |
| [DJED](https://github.com/DjedAlliance/Djed-Solidity)    | Stablecoin | [✅](https://iohk.io/en/research/library/papers/djed-a-formally-verified-crypto-backed-pegged-algorithmic-stablecoin/) | LUSTRE, Isabelle/HOL           |
| AMM                                                      | DEX        | [✅](https://github.com/dpusceddu/lean4-amm)                                                                           | Lean                           |
| [Morpho Blue](https://github.com/morpho-org/morpho-blue) | Lending    | [🏗️ WIP](https://github.com/Th0rgal/morpho-verity)                                                                     | Verity (Lean)                  |

## Formal Specifications & Semantics

- **[EVMYulLean](https://github.com/NethermindEth/EVMYulLean)** - Executable formal model of the EVM and Yul in Lean 4 ([blog](https://www.nethermind.io/blog/a-trustworthy-formal-model-of-evm-yul-in-lean))
- **[KEVM](https://github.com/runtimeverification/evm-semantics)** - Executable EVM semantics in the K Framework
- **[evm-sail](https://github.com/frisitano/evm-sail)** - Formal, executable EVM specification written in Sail, exportable to Lean, Rocq, Isabelle and HOL4 (WIP)
- **[evm-equivalence](https://github.com/runtimeverification/evm-equivalence)** - Per-opcode equivalence proofs between EVMYulLean and KEVM in Lean 4 (WIP)
- **[Etheorem](https://github.com/etheorem/etheorem)** - Executable Lean 4 implementation of the consensus specs (Fulu, Gloas, Heze), tested against `consensus-spec-tests`
- **[formal-leanSpec](https://github.com/NyxFoundation/formal-leanSpec)** - Lean 4 formalization of the Lean Consensus specification ([leanSpec](https://github.com/leanEthereum/leanSpec))
- **[riscv-zkvm](https://github.com/Verified-zkEVM/riscv-zkvm)** - Lean extraction of the official Sail RISC-V specification for zkVM verification, built on the [Lean backend for Sail](https://github.com/rems-project/lean-sail)

## Formal Verification Tools

### Production-Ready Tools

- **[Certora Prover](https://github.com/Certora/CertoraProver)** - Formal verification tool for EVM, Solana, and Stellar chains, [open source since February 2025](https://www.certora.com/blog/certora-goes-open-source)
- **[K Framework (KEVM)](https://github.com/runtimeverification/evm-semantics)** - Ethereum verification using K specifications
- **[Kontrol](https://github.com/runtimeverification/kontrol)** - Formal verification of Foundry tests using KEVM
- **[halmos](https://github.com/a16z/halmos)** - Symbolic testing tool for EVM smart contracts
- **[HEVM](https://github.com/argotorg/hevm)** - Symbolic EVM for symbolic execution, equivalence checking and formal verification
- **[SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html)** - SMT-based formal verification module built into the Solidity compiler
- **[Act](https://github.com/argotorg/act)** - Formal specification language for Ethereum smart contracts

### Emerging Tools

- **[Verity](https://github.com/lfglabs-dev/verity)** - Lean 4 EDSL for EVM smart contracts with a machine-checked compiler to Yul ([docs](https://veritylang.com))
- **[Isabelle/Solidity](https://isa-afp.org/entries/Isabelle-Solidity.html)** - Shallow embedding of Solidity in Isabelle/HOL with a verification condition generator (see also the [deep embedding](https://isa-afp.org/entries/Solidity.html))
- **[rocq-of-solidity](https://github.com/formal-land/rocq-of-solidity)** - Formal verification of Solidity smart contracts in Rocq
- **[rocq-of-python](https://github.com/formal-land/rocq-of-python)** - Converts Ethereum's Python specifications to Rocq (Coq) for formal verification (paused)
- **[Mythril](https://github.com/ConsenSysDiligence/mythril)** - Symbolic-execution-based security analysis tool for EVM bytecode
- **[solc-verify](https://github.com/SRI-CSL/solidity)** - Modular verifier for Solidity smart contracts based on Boogie (no updates since 2023)

### ZK Circuit Verification

- **[Picus](https://github.com/Veridise/Picus)** - Automated verification of the uniqueness (determinism) property of ZK circuits
- **[clean](https://github.com/Verified-zkEVM/clean)** - Lean 4 DSL for writing and verifying ZK circuits ([blog](https://blog.zksecurity.xyz/posts/clean))
- **[zkLean](https://github.com/GaloisInc/zkLean)** - Lean 4 DSL for ZK statements, with an extractor for Jolt
- **[LLZK](https://github.com/project-llzk/llzk-lib)** - MLIR-based intermediate representation for ZK circuits
- **[CertiPlonk](https://github.com/NethermindEth/CertiPlonk)** - Extraction and verification of Plonky3 constraint systems in Lean
- **[Garden](https://github.com/formal-land/garden)** - Formal verification of ZK circuits in Rocq
- **[zkvm-verus](https://github.com/CertiKProject/zkvm-verus)** - Evaluation of [Verus](https://github.com/verus-lang/verus) for zkVM/zkEVM verification
- **[VeIR](https://github.com/opencompl/veir)** - Verified MLIR-style compiler infrastructure in Lean, aimed at a verified ZK compiler toolchain

### Proof Libraries

- **[ArkLib](https://github.com/Verified-zkEVM/ArkLib)** - Formally verified interactive oracle reductions and SNARK components in Lean
- **[VCVio](https://github.com/Verified-zkEVM/VCVio)** - Lean framework for machine-checked cryptographic security proofs
- **[CompPoly](https://github.com/Verified-zkEVM/CompPoly)** - Computable polynomials in Lean
- **[iris-lean](https://github.com/Verified-zkEVM/iris-lean)** - Lean 4 port of the Iris separation logic framework

### Archived Tools

- **[Microsoft VeriSol](https://github.com/microsoft/verisol)** - Formal verifier for Solidity smart contracts (archived)
- **[Manticore](https://github.com/trailofbits/manticore)** - Symbolic execution tool for smart contracts (archived)
- **[Clear](https://github.com/NethermindEth/Clear)** - Lean framework for verifying Yul programs (archived)

## Security Reports

### Audit Portfolios

- **[Certora Security Reports](https://www.certora.com/reports)** - Comprehensive formal verification and audit reports for major Web3 protocols
- **[Runtime Verification Reports](https://runtimeverification.com/smartcontract)** - Formal verification reports for blockchain projects
- **[Trail of Bits Publications](https://blog.trailofbits.com/)** - Security research and formal methods applications

## Academic Research

### Research Projects

- **[Ethereum Formal Verification Overview](https://github.com/leonardoalt/ethereum_formal_verification_overview)** - Comprehensive overview of formal verification in the Ethereum ecosystem
- **[Verified zkEVM Project](https://verified-zkevm.org)** - Ethereum Foundation initiative funding formal verification of zkVMs, EVM implementations, and proof systems
- **[EthBench](https://github.com/seresistvanandras/EthBench)** - Formal verification benchmark for Ethereum smart contracts (no updates since 2017)
- **[Awesome Web3 Formal Verification](https://github.com/johnsonstephan/awesome-web3-formal-verification)** - Curated list of Web3 formal verification resources

### Academic Papers

- **[A Survey of Smart Contract Formal Verification](https://arxiv.org/abs/2008.02712)** - Comprehensive survey of formal verification techniques
- **[Jolt-QED: Formally Verifying Bytecode Expansions In Lean](https://eprint.iacr.org/2026/2157)** (2026) - Lean proofs of Jolt's RISC-V bytecode expansions
- **[Towards Automated Formal Verification of zkEVMs Using LLM-Guided Constraint Synthesis](https://arxiv.org/abs/2607.19795)** (2026) - VeriSynth: LLM-generated Python/Z3 models of Rust zkEVM opcode handlers
- **[A Rust-to-Lean Verification Pipeline with AI Provers: An Experience Report](https://arxiv.org/abs/2605.30106)** (2026) - Aeneas/Hax + ArkLib + AI provers applied to Plonky3 and RISC Zero primitives
- **[Verity: A Verified Compiler for a Core Fragment of EVM Smart Contracts in Lean 4](https://lfglabs.dev/papers/verity.pdf)** (2026) - Verified compilation chain from a Lean EDSL to Yul
- **[A Simplified Round-by-round Soundness Proof of FRI](https://eprint.iacr.org/2025/1993)** (2025) - Simplified RBR soundness proof of FRI, formalized in Lean ([blog](https://blog.zksecurity.xyz/posts/simple-rbr-fri/))
- **[Technical Report: Exploring Automatic Model-Checking of the Ethereum specification](https://arxiv.org/abs/2501.07958)** (2025) - Model checking Accountable Safety of 3SF with TLA+/Apalache
- **[Formal verification of safety properties of epoch processing in Beacon Chain](https://doi.org/10.1038/s41598-025-27396-w)** (2025, Scientific Reports) - Model checking of Beacon Chain epoch processing
- **[Formal Verification of Rewards and Penalties Mechanism of FFG Attestations: Ethereum 2.0 Beacon Chain Case Study](https://doi.org/10.1109/access.2025.3582822)** (2025, IEEE Access)
- **[Isabelle/Solidity: A deep embedding of Solidity in Isabelle/HOL](https://doi.org/10.1145/3700601)** (2025, Formal Aspects of Computing) - Executable denotational semantics of Solidity
- **[Certified Decision Procedures for Width-Independent Bitvector Predicates](https://doi.org/10.1145/3763148)** (OOPSLA 2025) - Verified bitvector automation in Lean
- **[Interactive Bitvector Reasoning using Verified Bit-Blasting](https://doi.org/10.1145/3763167)** (OOPSLA 2025) - Verified bit-blasting in Lean

## Vulnerability Detection

### Specific Vulnerability Research

- **[Reentrancy Verification](https://www.mdpi.com/2079-9292/12/10/2152)** - Reentrancy attack verification using Z3 SMT solver
- **[SmartScan](https://www.jatit.org/volumes/Vol103No3/4Vol103No3.pdf)** - Formal verification framework detecting 14 types of vulnerabilities

## Contributing

Contributions are welcome! Please follow the guidelines below.

### Guidelines

1. **Quality over quantity** - Only include high-quality, actively maintained projects
2. **Provide descriptions** - Each entry should have a clear, concise description
3. **Verify links** - Ensure all links are working and point to the correct resources
4. **Follow format** - Maintain consistent formatting throughout the list
5. **Stay relevant** - Focus on Ethereum and EVM-compatible formal verification

### How to Contribute

1. Fork this repository
2. Create a new branch for your additions
3. Add your entry in the appropriate section
4. Ensure your addition follows the format
5. Submit a pull request with a clear description

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related or neighboring rights to this work.

---

**Note**: This list is continuously updated. If you find any broken links or outdated information, please open an issue or submit a pull request.
