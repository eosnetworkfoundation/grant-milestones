# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/EOS-Cryptography-Proposal-2-b.md
* **Milestone Number:** 1
* **Milestone Payment Amount:** $55,000 USD
* **Contact Name:** Luka Percic
* **Contact email:** zeropass@pm.me

## Context
This delivery optimizes the current EC implementation in the ACK library and accelerate EC-based signature verification algorithms.
Moreover, this proposal also introduces SHA-384 hashing algorithm (commonly used with some EC, such as P-384).

## Deliverables
| Number | Deliverable | Link/Notes |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Documentation and step-by-step guide in [README.md](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md).  | 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 4 testnet](https://jungle4.eosq.eosnation.io/account/helloeosiock) the [example contract](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/examples/helloack).|
| 1. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/9) | Optimized EC point arithmetic by using Jacobian coordinate system and EC point multiplication with scalar by NAF method. Additionally, specific optimization was made for cases where elliptic curve has coefficient a=0 or a=-3 (secp256k1 and secp256r1, respectively).
| 2. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/9) | Added implementation of SHA-384 hash algorithm |

Benchmark:
curve     |  WASM OC    |  native | WASM OC a=0, a=-3 | native a=0, a=-3 |
| -----: |:-----------:|:--------:|:--------:| :--------:|
secp256k1 | 3.681 ms - 4.5 ms | 0.842 ms | 2.893 ms - 4.2 ms | 0.74 ms |     
secp256r1 | 4.17 ms - 5 ms  |  1.1220 ms | 3.664 ms - 4.9 ms | 1.03 ms |

Previous benchmark (*[EOS Cryptography Proposal 1-3](https://github.com/eosnetworkfoundation/grant-milestones/blob/f36ec75e137a401fd4c5899ca766351c9fa1e8fe/deliveries/eos-cryptography-proposal-1of2-3.md)*):
curve      |  WASM OC    |  native
| -----: | :-----------:|:--------:|
secp256k1 | ~6 ms | 1.1 ms      
secp256r1 | ~7 ms | 1.5 ms
