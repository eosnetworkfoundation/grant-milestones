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
| 0a. | License | [MIT LICENSE](https://github.com/ZeroPass/ack/blob/master/LICENSE) | 
| 0b. | Documentation | Documentation and step by step guide in [README.md](https://github.com/ZeroPass/ack/blob/master/README.md).| 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/ack/blob/master/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 4 testnet](https://jungle4.eosq.eosnation.io/tx/7ed2829fdb40463d03f0639ba7b18d8fa39b2d2e2b50a3d1a004f024901f13fc) the [example contract](https://jungle4.eosq.eosnation.io/account/helloeosiock). |
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
secp256k1 |   30+ ms  |   6-7 ms   |     1.2 ms      
secp256r1 |   30+ ms  |   7-8 ms   |     1.6 ms
* on a cheap VM (AMD) instance



**Bonus delivery**  
The modular exponentiation for RSA and RSASSA-PSS was moved from in library to the intrinsic, to further imrpove the preformance of Delivery 1 and Delivery 2.

**Additional Information**  
More detailed explanation will follow in the comment section below.