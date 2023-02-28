# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:**   
[https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md).
* **Milestone Number:** 3
* **Milestone Payment Amount:** $44,000 USD
* **Contact Name:** Luka Percic
* **Contact email:** zeropass@pm.me

**Context**  
General-purpose math primitives (i.e. addition, multiplication, inverse etc…) for elliptic curve arithmetics over a prime field, its example emplementation and benchmark.
This will allow defining higher-level cryptography EC algorithms (e.g. ECDSA verification algo) on custom elliptic curves in smart contract. The primitives will be built on top of the existing secure and audited EC cryptography library.

**Deliverables**

| Number | Deliverable | Link |
| -----: | ----------- | ------------- |
| 0a. | License | [MIT LICENSE](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/LICENSE) | 
| 0b. | Documentation | Documentation and step by step guide in [README.md](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md).| 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 3, Jungle 4 and CryptoKylin testnets](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md#testnet). |
| 1a. | [Antelope SDK library](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) | General-purpose math primitives (i.e. addition, multiplication, inverse etc…)  for elliptic curve arithmetics over an arbitrary finite field. Build inside EOSVM and using no OC flag |
| 1b. | [Antelope SDK library](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) | EOSIO SDK library | General-purpose math primitives (i.e. addition, multiplication, inverse etc…)  for elliptic curve arithmetics over an arbitrary finite field. Build inside EOSVM and using OC flag (optional*)|
| 2a. | [Antelope SDK library](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) |  Example implementation for **Secp256r1**. Build inside EOSVM and using no OC flag|
| 2b. | [Antelope SDK library](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) |  Example implementation for **Secp256r1**. Build inside EOSVM and using OC flag (optional*)|
| 31. | [Benchmark](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) | Benchmarking 2a to determine its viability for running it on the public EOSIO networks  |
| 3b. | [Benchmark](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) | Benchmarking 2b to determine its viability for running it on the public EOSIO networks  |

**as stated in the grant \*;** 
- If deliverable 1b will be preformant enough, we won't deliver deliver 1c, only deliverable 1a and 1b.

**Bonus delivery**; The modular exponentiation for RSA and RSASSA-PSS was moved from in library to the intrinsic, to further imrpove the preformance of Delivery 1 and Delivery 2.

**Additional Information**  
