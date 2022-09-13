# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:**   
[https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/eos-cryptography-proposal.md).
* **Milestone Number:** 2
* **Milestone Payment Amount:** $11,000 USD
* **Contact Name:** Luka Percic
* **Contact email:** zeropass@pm.me

**Context**  
RSASSA-PSS signature verification algorithm. It is a probabilistic and provably secure RSA signature scheme as opposed to RSA PKCS v1.5.  
All updated cryptosystems are switching to RSASSA-PSS.

**Deliverables**

| Number | Deliverable | Link | Notes |
| -----: | ----------- | ------------- |------------- |
| 0a. | License | [LICENSE](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/LICENSE) | MIT | 
| 0b. | Documentation | Documentation and step by step guide in [README.md](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md).| 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 3, Jungle 4 and CryptoKylin testnets](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca/README.md#testnet). |
| 1. | [Antelope SDK library](https://github.com/ZeroPass/antelope.ck/tree/688e6c97a2dd8d70784fec8f0f3cd3bef08b40ca) | Open-source cryptography library with RSA PKCS#1 v1.5 signature verification algorithm, RSASSA-PSS PKCS#1 v2.2 signature verification algorithm and Keccak hash algorithms: SHA3-256, SHA3-512, SHAKE-128 and SHAKE-256. |

**Additional Information**  
This milestone adds implementation of PKCS#1 v2.2 RSASSA-PSS signature verification algorithm with standard MGF1 mask generation function. Implementation is based on RFC 8017 https://www.rfc-editor.org/rfc/rfc8017. The modular exponentiation is still being done in the library (smart contract) due to specific intrinsic api in antelope cdt wasn't ready at the time of writing the implementation.
The project is only partly renamed from EOSIO. It will be fully renamed when cdt is to follow its naming conventions. Probably eosiock -> cdtck. 
