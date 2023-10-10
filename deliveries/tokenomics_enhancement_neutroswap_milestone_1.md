# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [Tokenomics Enhancement Neutroswap
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md)
* **Milestone Number:** 1

**Context:**
For *Milestone 1 - Smart Contract Development* completion

**Deliverables:**
- **Estimated duration:** 2 weeks
- **FTE:**  2
- **Costs:**  25,000 USD

| Number | Deliverable   | Link                                                                                                                                                                                                                                                                                                                                             | Notes    |
| -----: | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| 0a.    | License       | [LICENSE](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/LICENSE.md) |          |
| 0b.    | Documentation | https://docs.neutroswap.io/, https://github.com/neutroswap/neutroswap-v2-contracts | First link is to explain how how users can utilize all of the new updates works. The second one is a technical documentation of the smart contract for Neutroswap V2 |
| 0c.    | Unit Test     | [Unit Test](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main/test), [Unit Test Documentation](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main#-developer-guide) | |
| 1.     | Core Contracts | [Core Contract Repo](https://github.com/neutroswap/neutroswap-v2-contracts) | Unpacking smart contract requirements, migration plan for both subgraph and frontend, and integration testing plan |  
| 2.     | Tokenomics Contracts | [xNEUTRO Contract](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/src/tokens/XNeutroToken.sol) | xNEUTRO can only be redeem with vesting period. It will allow burning mechanism for $NEUTRO. However, $NEUTRO can be converted into $xNEUTRO in instant. |  
| 3.     | Plugins Contracts | [Plugins Contracts](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main/src/plugins) | Plugin contracts are enabling users to allocate their xNEUTRO into their desired plugins: Dividends, Yield boosters and other community plugins |  
| 4.     | Protocol Revenue Contracts | [NeutroMaster Contract](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/src/nft-pool-factory/NeutroMaster.sol) | This contract enables efficient distribution of rewards to $xNEUTRO holders. |  
