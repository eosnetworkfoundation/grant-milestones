# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:**   
[https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md).
* **Milestone Number:** 3
* **Milestone Payment Amount:** $44,000 USD
* **Contact Name:** Luka Percic
* **Contact email:** zeropass@pm.me

**Context**  
General-purpose math primitives (modular addition, multiplication, inverse etc…) for curve field element arithmetics and elliptic curve math primitives (point addition, multiplication etc...) for curve arithmetic over prime field GF(p), example implementation and benchmark.
This will allow defining higher-level EC cryptography algorithms (e.g. ECDSA verification) on custom elliptic curves GF(p) in smart contract.

**Deliverables**

| Number | Deliverable | Link/Notes |
| -----: | ----------- | ------------- |
| 0a. | License | [MIT LICENSE](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/LICENSE) | 
| 0b. | Documentation | Documentation and step by step guide in [README.md](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md).| 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 4 testnet](https://jungle4.eosq.eosnation.io/account/helloeosiock) the [example contract](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/examples/helloack). |
| 1a. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/5) | General-purpose math primitives (i.e. addition, multiplication, inverse etc…) for elliptic curve arithmetics over finite field GF(p). Build inside EOSVM and using no OC flag |
| 1b. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/5) | General-purpose math primitives (i.e. addition, multiplication, inverse etc…)  for elliptic curve arithmetics over an finite field GF(p). Build inside EOSVM and using OC flag (optional*)|
| 2a. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/5) |  Example implementation for **Secp256r1**. Build inside EOSVM and using no OC flag|
| 2b. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/5) |  Example implementation for **Secp256r1**. Build inside EOSVM and using OC flag (optional*)|
| 3a. | [Benchmark](https://jungle4.eosq.eosnation.io/tx/7ed2829fdb40463d03f0639ba7b18d8fa39b2d2e2b50a3d1a004f024901f13fc) | Benchmarking 2a to determine its viability for running it on the public Antelope networks  |
| 3b. | [Benchmark](https://jungle4.eosq.eosnation.io/tx/7c902de7cc2ee4c9609a0c3a2e7f71da52c8a12ff20ca11e356ce0fb7edfd8f9) | Benchmarking 2b to determine its viability for running it on the public Antelope networks  |

 OC implementation turned out to be performant enough (<10ms) all deliverables are implemented to and including .b points (1.b, 2.b, 3.b).

*as stated in the grant:   
*If deliverable 1b will be preformant enough, we won't deliver deliver 1c, only deliverable 1a and 1b. Same logic applies to coresponding Example implementation for Secp256r1 and their benchmarking.*

curve      |  WASM    |  WASM OC    |     native reference
| -----: |:------------:|:-----------:|:--------:|
secp256k1 |   30+ ms  |   ~6 ms   |     1.1 ms      
secp256r1 |   30+ ms  |   ~7 ms   |     1.5 ms

*The benchmarking results were obtained by averaging the time taken for verifying 1 ECDSA signature on a cheap VM instance (AMD)*

**Bonus delivery**  
- Implementation of ECDSA signature verification algorithm.
- To further imrpove the preformance of Delivery 1 and Delivery 2 the modular exponentiation for RSA & RSASSA-PSS was moved from in library to the intrinsic.

**Additional Information**  
#### R & D
The research began with an attempt to find an existing EC library that would be efficient enough to use in AntelopeIO WASM. The following libraries were examined:

- OpenSSL (and its derivatives): Not tested for compilation in wasm. Our initial research showed that it may be too complex to extract only the required code for EC, and would be difficult to maintain code with upstream.

- [libecc](https://github.com/libecc/libecc): Not optimized for speed.

- [CryptoPP](https://github.com/weidai11/cryptopp): Too complex for modification. Requires RTTI and exceptions to be available. Also, a lot of specializations is done per platform (assembly) which could result is slower code for wasm (same considerations as OpenSSL)

- [Botan](https://github.com/randombit/botan): Too complex for modification. Requires exceptions to be available. Also, a lot of specializations is done per platform (assembly) which could result is slower code for wasm (same considerations as CryptoPP)

- [micro-ecc](https://github.com/kmackay/micro-ecc): Lightweight ECC library with optimized implementation of ECDSA signature verification algorithm: points are represented in jacobian coordinate system, Shamir's trick for 2x point scalar multiplication & addition (u1\*G + u2\*Q), co-Z point addition etc... Implementation of integer arithmetics avoids heap allocation. Fast ECDSA verification when elliptic curve specific optimizations are enabled.

    **Cons**:
     - Curve-specific optimization for fast modular multiplication and doubling.
     - The implementation assumes curve parameter a=-3 (NIST curves) or a=0 (secp256k1), which means that it cannot be applied to any GF(p) curves, such as brainpool curves.
     - Some general modular operations such as modulo and modular multiplication are very slow, even when OC is enabled (5.5ms-11ms).  
     - Per curve specialized double jacobian multiplication.
     - Difficult to maintain code due to raw structures (e.g. point coordinates are represented as a continuous 1D array point[64] = {x, y}), which can be prone to unintentional bugs.

- [mcl](https://github.com/herumi/mcl): The implementation of large integer arithmetics is better optimized for speed, avoiding heap allocation and utilizing optimized arithmetic algorithms for addition, subtraction, multiplication, division, modulo, and modular inverse operations.  
   General arithmetics for large integers are still too slow in pure WASM environment. When OC is enabled, the arithmetic speed depends on the system it runs and system load.

   **Cons**: Very slow EC initialization due to full curve validation. Even with OC enable transaction can subjective fail due to exceeding CPU usage limit.

After testing those libraries, [micro-ecc](https://github.com/kmackay/micro-ecc) was combined with implementation of integer and modular arithmetic from the [mcl](https://github.com/herumi/mcl) library to test if the performance could be improved for general case (EC point doubling was still per curve dependant). Running ECDSA signature verification benchmark tests in AntelopeIO showed very promising results:

- micro-ecc library with all EC optimization (mmod_fast)
  curve     | WASM OC    |
  | ------: |:-----------:|
  secp256k1 |   ~2.4 ms - 4.7ms
  secp256r1 |   ~1.2 ms - 4 ms 

- micro-ecc library with general modulo operator (uECC_vli_mmod)
  curve     | WASM OC    |
  | ------: |:-----------:|
  secp256k1 |   ~5.5 ms - 7.8 ms
  secp256r1 |   ~9.2 ms - 11 ms 

- micro-ecc library + mcl large integer [VInt](https://github.com/herumi/mcl/blob/master/include/mcl/vint.hpp)
  curve     | WASM OC    |
  | ------: |:-----------:|
  secp256k1 |   ~3 ms - 4.7 ms
  secp256r1 |   ~2 ms - 4 ms

*Note, in all cases point doubling was done using curve specific optimization (double_jacobian).*

Tests using 64 bit integer as base unit for internal representation of large integer was also performed on EC optimized micro-ecc library:
curve     | WASM OC    |
| ------: |:-----------:|
secp256k1 |   ~6.6 ms - 8.7 ms
secp256r1 |   ~4.5 ms - 8 ms 

As expected, using 64 bit integer as base was slower than 32 bit integer (~2x slower) causing no ECDSA verification to complete in transaction execution bound time (<30ms) when all curve specific optimization were disabled.

#### Implementation of general EC arithmetics & ECDSA verification 
After identifying a fast, multipurpose implementation of large integers, the decision was made to use it as the basis for general integer arithmetic and to build the required EC components around it. This conclusion was based on the fact that the EC arithmetic implementation in the [micro-ecc](https://github.com/kmackay/micro-ecc) library can be difficult to understand and use properly. Additionally, there are existing issues with the library ([#128](https://github.com/kmackay/micro-ecc/issues/128), [#141](https://github.com/kmackay/micro-ecc/issues/141), [#196](https://github.com/kmackay/micro-ecc/issues/196), [#203](https://github.com/kmackay/micro-ecc/issues/203)), which raises concerns that the library may not be well-maintained. (For reference, EC validity in the ack library is tested using the same [NIST test vectors & Wycheproof testvectors](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/tests/include/ack/tests/ecdsa_secp256r1_test.hpp)).

There was also requirement for simpler interface for basic EC operation (G+Q,s\*Q etc...) where you wouldn't need to use specific specialized functions to do the EC arithmetics which should improve code readability in the smart contract.
For this, the basic modular arithmetic code was written first and then implementation of EC over GF(p) with points in affine and projective (homogeneous) coordinate systems. The ECDSA signature verification algorithm was written on top of this to test the efficiency of the implementation. Using EC arithmetic in projective coordinate system resulted in approximately a two-fold increase in verification speed, suggesting that further optimization of the ECDSA algorithm could bring verification time to well under 10 ms in a WASM environment with OC enabled. The Shamir's trick algorithm was selected for this task, which optimizes multiplying and addition of 2 points (u1\*G + u2\*Q) in 1 go, slashing the slashing verification times by ~2. As demonstrated by the benchmark tables below, this approach proved to be effective in achieving the milestone goal, and therefore no further optimization was pursued.

Note, to further optimize current implementation, it may be worthwhile to eliminate the need for OC first by implementing basic modular arithmetic functions as host functions (intrinsics) in future milestones.

* ECDSA verification affine points
    curve    |    WASM OC    |     native reference
    | -----: |:------------:|:--------:|
    secp256k1 |    ~25-30+ ms   |    7.7 ms
    secp256r1 |    ~26-30+ ms   |    7.8 ms

* ECDSA verification affine points and  
  using Shamir's trick for fast multiplication and addition of u1\*G + u2\*Q 
    curve    |    WASM OC    |     native reference
    | -----: |:------------:|:--------:|
    secp256k1 |    ~17.9 ms   |    4.6 ms
    secp256r1 |    ~18.0 ms   |    4.7 ms

* ECDSA verification in homogeneous coordinate system (`ec_point_fp_proj`)
    curve    |    WASM OC    |     native reference
    | -----: |:------------:|:--------:|
    secp256k1 |    ~9.5 ms   |     2 ms
    secp256r1 |    ~12.2 ms   |    2.8 ms

* ECDSA verification in homogeneous coordinate system (`ec_point_fp_proj`)  and  
  using Shamir's trick for fast multiplication and addition of u1\*G + u2\*Q 
    curve      |  WASM OC    |     native reference
    | -----: |:-----------:|:--------:|
    secp256k1 |   ~6 ms   |     1.1 ms
    secp256r1 |   ~7 ms   |     1.5 ms

*Note, all benchmarking results were obtained by averaging the time taken for verifying 1 ECDSA signature on a cheap VM instance (AMD)*
