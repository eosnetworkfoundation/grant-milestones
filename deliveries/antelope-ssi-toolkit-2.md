# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** <https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/ssi-toolkit-verifiable-credentials.md>
* **Milestone Number:** 2
* **Milestone Payment Amount:** $18,000 USD
* **Contact Name:** Jack Tanner
* **Contact email:** contact@tonomy.foundation

**Deliverables**

| Number | Deliverable | Link | Notes |
| ------------- | ------------- | ------------- |------------- |
| 1. | npm | <https://www.npmjs.com/package/@tonomy/antelope-ssi-toolkit> |  |
| 1. | article | <https://blog.tonomy.foundation/issue-and-verifying-verifiable-credentials-with-an-antelope-account-d1b4e76bfba0> and <https://blog.tonomy.foundation/verifiable-credentials-with-provable-delegated-and-multi-sig-signatures-e46ca74d7d87> |  |
| 1. | Implementation of verify() function | <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/blob/d329fe93493e262f16d0e80fd89c1f5fb2fddceb/src/credentials.ts#L49> |  |
| 2. | Documentation and publish | [github.com/Tonomy-Foundation/Antelope-SSI-Toolkit](https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/tree/d329fe93493e262f16d0e80fd89c1f5fb2fddceb) and <https://www.npmjs.com/package/@tonomy/antelope-ssi-toolkit> |  |

**Definition of done for issue()**

Definition of done for verify()

* [x] the verify function from the chosen VC library successfully validates a VC from an Antelope account with permission of 1 key
* [x] the verify function from the chosen VC library successfully validates a VC from an Antelope account with permission of 1 account delegation
* [x] the verify function from the chosen VC library successfully validates a VC from an Antelope account with permission of 2 threshold, 3 keys
* [x] the verify function from the chosen VC library successfully validates a VC from an Antelope account with permission of 3 threshold, 2 keys and 2 account delegations
* [x] 4x unit test showing the above tasks

See <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/blob/d329fe93493e262f16d0e80fd89c1f5fb2fddceb/test/credentials.test.ts>
and <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/blob/d329fe93493e262f16d0e80fd89c1f5fb2fddceb/test/did-jwt-vc.test.ts>
