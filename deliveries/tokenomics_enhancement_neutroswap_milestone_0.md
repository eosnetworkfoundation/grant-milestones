# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [Tokenomics Enhancement Neutroswap
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/tokenomics_enhancement_neutroswap.md)
* **Milestone Number:** 0

**Context:**
For *Milestone 0 - Requirement Analysis* completion

**Deliverables:**
- **Estimated duration:** 2 weeks
- **FTE:**  2
- **Costs:**  5,000 USD

| Number | Deliverable | Link                                                                                                                                                                                                                                                                                                                                            | Notes    |
| -----: | ----------- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| 0a. | License | MIT |  |
| 0b. | Threads | [Twitter Thread](https://typefully.com/t/GWAxzwj) | The link given here is just a typefully draft and will be released to the public at our marketing schedule |
| 1. | General Requirement and Migration Plan | Within this document | Unpacking smart contract requirements, migration plan for both subgraph and frontend, and integration testing plan |  
| 2. | Documentation | [Neutroswap V2 Docs](https://docs.neutroswap.io/neutroswap-v2-coming-soon/staked-positions-spnfts), [Neutroswap V2 Contract Docs](https://github.com/Nava-Labs/neutroswap-v2/blob/main/README.md) | For an extensive understanding of Neutroswap v2, please refer to our [Documentation](https://docs.neutroswap.io) |  

## General Requirement and Migration Plan
This document serves as an introduction to the general requirements and migration plan for a decentralized application. It aims to provide an outline for developers, project managers, and stakeholders to navigate the complexities of building and migrating to Neutroswap V2 effectively.

### Smart contract Requirement
Neutroswap V2 will introduce multiple contract that support our V2 tokenomics like plugins, NFT-based position, and launchpad. 
For an extensive understanding of Neutroswap v2, please refer to our [Documentation](https://docs.neutroswap.io). 
Below are the list of new Neutroswap V2 contract:

- **xNEUTRO**<br/>
  The locked version and non-transferrable token of $NEUTRO with the purpose of providing utility for users by allocating xNEUTRO to various provided Plugins.

- **NeutroMaster**<br/> 
  Centralizes Neutro's yield incentives distribution.

- **NFTPoolFactory**<br/>
  Factory pattern for creating NFT Pool.

- **NFTPool**<br/>
  Wraps ERC20 assets into non-fungible staking positions called spNFTs. Yield-generating positions when the NFTPool contract has allocations from the Neutro Master.

- **NitroPoolFactory**<br/> 
  Factory pattern for creating Nitro Pool.

- **NitroPool**<br/> 
  spNFTs Pool for incentives position based on the determined position requirements and purposed for collaborating with other projects.

- **Dividends**<br/> 
  Neutroswap Plugin to distribute dividends to xNEUTRO allocators.

- **YieldBooster**<br/>
  Neutroswap Plugin to boost spNFTs' yield (staking positions on NFTPools).

- **FairAuctionFactory**<br/> 
  Factory pattern for creating Fair Auction (launchpad).

- **NeutroHelper**<br/> 
  Serving data to the frontend, for example to calculate APR, dollar value of the pool, and etc.

> No changes required on our legacy contract, but the introduction of V2 tokenomics require some adjustment on $NEUTRO emission stored in our ERC-20 variables

### Subgraph Migration Plan
WIP

### High Fidelity Prototype
Neutroswap V2 high fidelity prototype is available [here](https://www.figma.com/file/gkw76rgPT3CWqALsY51FEq/Neutroswap-V2-High-Fidelity-Prototype?type=design&node-id=0%3A1&mode=design&t=lZmmvo17eMou581J-1)

### Front-end Migration Plan
After long code review, we found multiple changes that are required for the app maintanability. We acknowledge that everything listed below is non intrusive and not required for the Neutroswap V2 launch, it is better to list them here for the app maintanability

- [ ] NextJS 13 introduced the `app` directory but `pages` directory isn’t deprecated yet
- [ ] Bump `wagmi` to latest (uses `viem` instead of `ethers`)
- [ ] Bump `viem` to latest
- [ ] Migrate all `ethers` to use `viem`
- [ ] Migrate all `BigNumber` to `BigInt`
 
### Integration Testing Plan
- [ ] Prepare the test case that covers V2 features
- [ ] Prepare the test environtment and test data
- [ ] Launch V2 features on testnet, and integrate all existing contract to the V2 features
- [ ] Execute the integration testing and create a integration testing report

>
