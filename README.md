# Solana is a zk chain
Solana stands out as a highly capable Layer 1 (L1) blockchain, especially for those looking to develop zero-knowledge (ZK) applications. Below is a list of great zk resources, but first why Solana?

A key aspect of Solana's suitability for ZK applications is its runtime support for elliptic curve operations. Elliptic curve cryptography (ECC) is a cornerstone in the construction of ZK proofs, which enable one party to prove the truth of a statement to another party without revealing any underlying data. Solana's native support for these operations significantly simplifies the development process, allowing for more efficient and secure implementation of ZK proofs.

Another major advantage of Solana is its low fee compute and transaction model. In the blockchain world, transaction costs can be a substantial hurdle, affecting scalability and user adoption. Solana addresses this challenge with its high-throughput consensus mechanism, which facilitates fast and cost-effective transactions. This efficiency is particularly beneficial for ZK applications, which often require numerous transactions to maintain their privacy and security features.

Moreover, Solana offers innovative solutions for managing state in ZK applications. In instances where applications cannot fully utilize Solana's new syscalls for curves, the platform's low transaction costs come to the rescue. Developers can leverage these low costs to process verifier computations over state efficiently. This approach allows for the recording of necessary data and the subsequent removal of excess state, optimizing the application's performance and resource usage.

In summary, Solana presents a compelling combination of technical capabilities for ZK application development. Its support for elliptic curve operations, coupled with a low-cost transaction model, makes it an attractive platform for developers looking to explore the frontiers of privacy and security in blockchain technology. While I am not an official representative of Solana, the platform's features speak for themselves, positioning it as a leading choice for building sophisticated and efficient ZK applications.

## Solana ZK features

### Runtime features
All the available syscalls are here [Syscalls](https://github.com/solana-labs/solana/blob/501458a7daa023eb2c64a18d54ad618d4305af68/sdk/program/src/syscalls/definitions.rs#L65).

Syscalls allow these computations to be cheaper within the SVM.
Notably
* Barreto-Naehrig Curve/Group operations - [Curve/Group](https://github.com/solana-labs/solana/blob/501458a7daa023eb2c64a18d54ad618d4305af68/sdk/program/src/alt_bn128/mod.rs)
* 21559 Ristretto and Edwards Curve/Group Operations: example of using them I cant find the impl code  - [Curve/Group](https://github.com/solana-labs/solana/tree/501458a7daa023eb2c64a18d54ad618d4305af68/zk-token-sdk/src/curve25519) see edwards and ristretto rust modules.
* Poseidon Hash Function Syscall - [Hash](https://github.com/solana-labs/solana/blob/501458a7daa023eb2c64a18d54ad618d4305af68/sdk/program/src/poseidon.rs#L170) (to be activated in [v1.17](https://github.com/solana-labs/solana/issues/33073))
* Altbn128 [Syscall](https://github.com/ananas-block/solana/blob/master/sdk/program/src/alt_bn128.rs) - cheap elliptic curve operations over the bn256(bn254/alt-bn128) curve. Supported operations are equivalent to EVM's bn256add, bn256ScalarMult, and bn256Pairing. (to be activated in [v1.17](https://github.com/solana-labs/solana/issues/33398))
* Altbn128 g1 & g2 compression [Syscall](https://github.com/solana-labs/solana/blob/master/sdk/program/src/alt_bn128/compression.rs) - Halves groth16 proof bytes sent on-chain to 128b. (to be activated in [v1.17](https://github.com/solana-labs/solana/issues/33398))

### Solana Vended Contracts/Programs  

* zk token program - [Solana Docs](https://docs.solana.com/developing/runtime-facilities/zk-token-proof)
* Stealth ,Written by a former solana labs employee Larry Wu [Stealth](https://github.com/metaplex-foundation/metaplex-incubating-programs/tree/main/stealth) not strictly ZK but a good look at how to crank math over multuple transactions.

### Solana Ecosystem Zk Projects
* Elusiv - [V1 Verifier Contract](https://github.com/elusiv-privacy/elusiv/blob/master/elusiv/src/instruction.rs) 
* Light Protocol - A ZK layer for general-purpose private smart contract (PSP) execution. [Repo](https://github.com/Lightprotocol/light-protocol) also [docs](https://docs.lightprotocol.com/core-concepts/lifecycle-of-a-light-transaction)
  * [Groth16 Verifier ](https://github.com/Lightprotocol/groth16-solana) (This verifier is compatible with the altbn128 syscalls)
  * [Light-Poseidon](https://crates.io/crates/light-poseidon) (Used by Solana)
  * [Macro-Circom](https://github.com/Lightprotocol/light-protocol/blob/main/macro-circom/src/main.rs) (Macros for the Circom language, used by PSPs built with Light)
  * [Sparse merkle-tree implementation](https://github.com/Lightprotocol/light-protocol/blob/main/merkle-tree/src/lib.rs) (compatible with the Poseidon hash syscall)
  * [Reference implementation](https://github.com/Lightprotocol/breakpoint-workshop) for an encrypted swap PSP.
    
* Another Groth16 [Verifier ](https://github.com/aneopsy/groth16-sol-verifier/blob/main/README.md)
* Yet another Groth16 [Verifier](https://github.com/zkLinkProtocol/groth16-sol-verifier)
* Possibly some good examples of varios proof systems relating to solana [Click Here](https://github.com/umi-ag/sion/tree/alpha/crates-solana)

