# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** <https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/ssi-toolkit-verifiable-credentials.md>
* **Milestone Number:** 1
* **Milestone Payment Amount:** $18,000 USD
* **Contact Name:** Jack Tanner
* **Contact email:** jack@tonomy.foundation

**Deliverables**

| Number | Deliverable | Link | Notes |
| ------------- | ------------- | ------------- |------------- |
| 1. | Environment setup | NA | We discussed and realized that a running Antelope was not needed, and adds extra burden on developers to be able to test. In milestone 2 we will be using programmed DID Documents to test against. |
| 2.  | Decision for Verifiable Credential library | <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/issues/17#issuecomment-1263319391> | NA|
| 3. | Implementation of W3C Vrifiable Condition | <https://github.com/Tonomy-Foundation/did-jwt> and <https://github.com/Tonomy-Foundation/did-jwt-vc> | The bulk of this work was done in the forked `did-jwt` (see PRs #1 and #2) and `did-jwt-vc` (see PR #1). Check out the PRs for the changes made from the original forked repositories. |
| 4. | Implementation of issue() function | <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/blob/820748442e11ec6fe6da0b2c344ee0dc7cb45665/src/credentials.ts#L32> | see the "Definition of done" in <https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/ssi-toolkit-verifiable-credentials.md#milestone-1-verifiable-credential-issue> copied below |

**Definition of done for issue()**

* [x] the issued VC contains a proof object that complies to the W3C standard
* [x] this object contains a valid signature that encapsulates the data from the VC
* [x] 2x unit test showing the above two tasks

See <https://github.com/Tonomy-Foundation/Antelope-SSI-Toolkit/blob/820748442e11ec6fe6da0b2c344ee0dc7cb45665/test/credentials.test.ts>
