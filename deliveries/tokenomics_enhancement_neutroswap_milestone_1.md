# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [Tokenomics Enhancement Neutroswap
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md#eos-network-foundation-grant-proposal)
* **Milestone Number:** 1 & 2

**Context:**
For *[Milestone 1 - Smart Contract Development](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md#milestone-1---smart-contract-development)* and *[Milestone 2 - Graph Node Deployment, Subgraphs, and Web Development](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md#milestone-1---smart-contract-development)* completion

#### 📜 Overview Neutroswap V2 Contracts

- **xNEUTRO:** The locked version and non-transferrable token of $NEUTRO with the purpose of providing utility for users by allocating xNEUTRO to various provided Plugins.
- **NeutroMaster:** Centralizes Neutro's yield incentives distribution.
- **NFTPoolFactory:** Factory pattern for creating NFT Pool.
- **NFTPool:** Wraps ERC20 assets into non-fungible staking positions called spNFTs. Yield-generating positions when the
  NFTPool contract has allocations from the Neutro Master.
- **NitroPoolFactory:** Factory pattern for creating Nitro Pool.
- **NitroPool:** spNFTs Pool for incentives position based on the determined position requirements and purposed for
  collaborating with other projects.
- **Dividends:** Plugin to distribute dividends to xNEUTRO allocators.
- **YieldBooster:** Plugin to boost spNFTs' yield (staking positions on NFTPools).
- **FairAuctionFactory:** Factory pattern for creating Fair Auction.
- **NeutroHelper:** Serving FE datas.

**Deliverables:**
- **Estimated duration:** 8 weeks
- **FTE:**  4
- **Costs:**  40,000 USD

| Number | Deliverable   | Link                                                                                                                                                                                                                                                                                                                                             | Notes    |
| -----: | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| 0a.    | License       | [LICENSE](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/LICENSE.md) |          |
| 0b.    | Documentation | [Docs](https://docs.neutroswap.io/) <br /> [Neutroswap V2 contracts](https://github.com/neutroswap/neutroswap-v2-contracts) | First link is to explain how how users can utilize all of the new updates works. The second one is a technical documentation of the smart contract for Neutroswap V2. |
| 0c.    | Unit Test     | [Unit Test](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main/test) <br /> [Unit Test Documentation](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main#-developer-guide) | All smart contracts for Neutroswap V2 have undergone testing using the Foundry package. |
| 0d.    | Testing Guide     | [Guide](https://github.com/neutroswap/neutroswap-v2-contracts?tab=readme-ov-file#-developer-guide) | The testing guide will be updated periodically following any changes we've made during development. |
| 0e.    | Integration Tests     | [Test Report](https://github.com/neutroswap/neutroswap-app/blob/dev/TESTREPORT.md) | Conducted tests on the functionality and user experience of the Neutroswap app website, ensuring that the integration of the smart contract with the website is seamless and meets the predetermined requirements. | 
| 1.     | Core Contracts | [Core Contract Repo](https://github.com/neutroswap/neutroswap-v2-contracts) | Unpacking smart contract requirements, migration plan for both subgraph and frontend, and integration testing plan |  
| 2.     | Tokenomics Contracts | [xNEUTRO Contract](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/src/tokens/XNeutroToken.sol) | xNEUTRO can only be redeem with vesting period. It will allow burning mechanism for $NEUTRO. However, $NEUTRO can be converted into $xNEUTRO in instant. |  
| 3.     | Plugins Contracts | [Plugins Contracts](https://github.com/neutroswap/neutroswap-v2-contracts/tree/main/src/plugins) | Plugin contracts are enabling users to allocate their xNEUTRO into their desired plugins: Dividends, Yield boosters and other community plugins |  
| 4.     | Protocol Revenue Contracts | [NeutroMaster Contract](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/src/nft-pool-factory/NeutroMaster.sol) | This contract enables efficient distribution of rewards to $xNEUTRO holders. |  
| 5.     | Subgraph Development | [Factory Graph](https://testnet.dbi.foundation/subgraphs/name/neutro-amm) <br /> [Launchpad Graph](http://testnet.dbi.foundation/subgraphs/name/neutro-launchpad) <br /> [spNFT Graph](http://testnet.dbi.foundation/subgraphs/name/neutro-nftPool)| We've published three public subgraphs for Neutroswap data indexing. |  
| 6.     | New V2 UI | [NeutroswapV2 UI](https://testnet-app.neutroswap.io/) <br /> [Front End Repository](https://github.com/neutroswap/neutroswap-app/tree/dev) | We've Implemented the V2 high-fidelity UI prototype from earlier stage, while also added new components necessary in enabling users to interact will all of the new updates and keeping the current UI accessible to all users. |  
| 7.     | Analytics | [Neutroswap Analytis Page](https://testnet-analytics.neutroswap.io/) | We've created a dedivated analytics page enabling users to see xNEUTRO, spNFTs, and activity in all of the new contracts. |  
| 8.     | Testnet Deployment | [Smart Contracts](https://github.com/neutroswap/neutroswap-v2-contracts?tab=readme-ov-file#testnet-contracts) | We've deployed new contract, subgraphs, and web to the EOSEVM Testnet environment. |  
