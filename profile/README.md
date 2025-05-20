# Lattirust
Lattirust is a Rust library for lattice-based zero-knowledge/succinct arguments. It is intended to be somewhat like [arkworks](https://github.com/arkworks-rs), but for lattices; or, alternatively, like [lattigo](https://github.com/tuneinsight/lattigo), but for arguments. In short, lattirust provides an extensive toolbox for lattice-based primitives, implementations of state-of-the-art schemes, and makes it easy to prototype, test, and benchmark new schemes. All the code is dual-licensed under an MIT and an Apache v2 license, at your discretion. 

Lattirust is maintained by [Christian Knabenhans](https://cknabs.github.io). Issues, feedback, and contributions are welcome. 

## Contents
Lattirust provides the following crates. 

### `lattirust-arithmetic`
[lattirust-arithmetic](https://github.com/lattirust/lattirust/tree/main/lattirust-arithmetic) implements (arkworks-compatible) rings and fields, polynomial rings, challenge spaces, linear algebra tools, and interfaces with [nimue](https://github.com/arkworks-rs/nimue).

### `lattice-estimator`
[lattice-estimator](https://github.com/lattirust/lattirust/blob/main/lattice-estimator) provides concrete security estimates for lattice problems, which can be used to set parameters for schemes. Currently, these estimates are based on the [lattice estimator](https://github.com/malb/lattice-estimator) and on PQ-Crystals' [security-estimates](https://github.com/pq-crystals/security-estimates). In the near future, we plan to have a Rust-based estimator, which will speed up parameter selection.

### `relations`
[relations](https://github.com/lattirust/lattirust/blob/main/relations) defines interfaces for relations and reductions, lattice-friendly relations (e.g., LaBRADOR's principal relation), and interfaces with arkworks' relations. 

### `labrador`
[labrador](https://github.com/lattirust/labrador) implements the [LaBRADOR](https://eprint.iacr.org/2022/1341) lattice-based argument. 

### `lova`
[lova](https://github.com/lattirust/lova) implements the [Lova](https://eprint.iacr.org/2024/1964) lattice-based folding scheme. 

## Roadmap

### Lattice arithmetic
We plan to implement polynomial operations for more polynomial rings, including non-NTT- or partial-NTT-based polynomial multiplication, lifting techniques for polynomial rings with modulus $q=5 \mod 8$. 

### Lattice estimator
Existing lattice estimator are tailored to {M,R,}LWE assumptions, whereas arguments typically require {M,R,v,I,k-R,}SIS assumptions. Further, existing estimators are written in Sage, whereas for efficiency reasons it would be preferable to have a const implementation in Rust, that can be called at compile-time. We have implemented our own customized lattice estimator (following state-of-the-art attacks), and we will merge it soon. 

### Latticefold
[Nethermind's implementation of latticefold](https://github.com/NethermindEth/latticefold) is built on a fork of (an early version of) lattirust, and we plan to upstream their implementation back into lattirust. 

### More schemes
We plan to implement additional schemes (e.g., [Greyhound](https://eprint.iacr.org/2024/1293), as well as new schemes that we are currently working on) in the near future. 

### Proof-of-encryption
We are currently implementing two proofs of {M,R,}LWE encryption ([KLSS23](https://eprint.iacr.org/2023/623) and [Libert24](https://eprint.iacr.org/2023/800)), which we will also open-source soon. 

### High-assurance
We are currently implementing client-side fully homomorphic encryption (FHE) operations in [Jasmin](https://github.com/jasmin-lang/jasmin), and are formally verifying that they are constant-time. This implementation will also live under the lattirust umbrelly, although it is slightly off-topic. However, we plan to have other high-assurance implementations and proofs for the core lattirust ecosystem. Concretely, we're thinking about implementations of critical parts in [hacspec](https://hacspec.org/) and/or [Jasmin](https://github.com/jasmin-lang/jasmin), as well as EasyCrypt/Lean proofs for core technical lemmas that are used in many lattice-based arguments. 
