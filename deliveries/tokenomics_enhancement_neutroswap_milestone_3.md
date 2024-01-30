# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [Tokenomics Enhancement Neutroswap
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md#milestone-3---mainnet-deployment--marketing)
* **Milestone Number:** 3

**Context:**
For *[Milestone 3 - Mainnet Deployment & Marketing](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md#milestone-3---mainnet-deployment--marketing)* completion

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
- **Estimated duration:** 2 weeks
- **FTE:**  2
- **Costs:**  5,000 USD

| Number | Deliverable   | Link                                                                                                                                                                                                                                                                                                                                             | Notes    |
| -----: | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| 0a.    | License | [LICENSE](https://github.com/neutroswap/neutroswap-v2-contracts/blob/main/LICENSE.md) |          |
| 0b.    | Article | [Neutroswap V2 Introduction Thread](https://x.com/Neutroswap/status/1750911285938753575?s=20) | We published an informative threads on twitter, explaining the concept of V2 smart contracts and how they will be utilized within our project. |
| 1.    | Smart Contract Deployment | [Mainnet Smart Contract List](https://github.com/neutroswap/neutroswap-v2-contracts?tab=readme-ov-file#mainnet-contracts) | We've deployed all contract necessary for V2 upgrade on EOS-EVM mainnet. |
| 2.    | Smart Contract Code Verification | [Mainnet Smart Contract List](https://github.com/neutroswap/neutroswap-v2-contracts?tab=readme-ov-file#mainnet-contracts) | We've verified the smart contract codes on official EOS-EVM mainnet Explorer by providing ABIs, bytecodes, and contract addresses. |
| 3.    | Graph Node Deployment	 | [Graph Index & Query Node](https://dbi.foundation/) | We've published a private graph-node instance for the EOS-EVM mainnet environment. | 
| 4.     | Subgraph Deployment	 | [Factory Graph](https://mainnet.dbi.foundation/subgraphs/name/neutro-amm) <br /> [Launchpad Graph](http://mainnet.dbi.foundation/subgraphs/name/neutro-launchpad) <br /> [spNFT Graph](http://mainnet.dbi.foundation/subgraphs/name/neutro-nftPool) [Neutroswap Subgraph Repo](https://github.com/neutroswap/neutro-amm-subgraph)| We've published public subgraphs for Neutroswap updates and start indexing EOS-EVM mainnet. |  
| 5.     | New UI Deployment |  [Neutroswap App](https://app.neutroswap.io/) <br /> [Neutroswap App Repo](https://github.com/neutroswap/neutroswap-app) | We've deployed the new UI to Production. |
