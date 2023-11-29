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
| 1. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/9) | Optimized EC arithmetic by using Jacobian coordinate system and EC point multiplication with scalar by NAF method.
| 2. | [Antelope SDK library](https://github.com/ZeroPass/ack/pull/9) | Sha-384 |

Current benchmarks:
curve     |  WASM OC    |     native reference
| -----: |:-----------:|:--------:|
secp256k1 |     4.229 ms   |     0.92 ms      
secp256r1 |    4.621 ms   |     1.15 ms


## Additional Information
We are still planning some small optimizations for the second milestone.
