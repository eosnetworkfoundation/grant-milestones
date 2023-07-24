 Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** [FACINGS NFT Collection Manager Stage 2](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/facings-nft-collection-manager-stage-2.md)
* **Milestone Number:** 1
* **Milestone Payment Amount:** $80,000 USD
* **Contact Name:** Rob Konsdorf
* **Contact email:** rob@facings.io

**Context** (optional)
The deliverables in this first milestone represent three main features: (1) TypeScript migration, (2) UX improvements, and (3) plugin framework for the NFT Collection Manager.

**Deliverables**

| Number | Deliverable         | Link                                                                          | Notes                                                                       |
| -----: | ------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 0a.    | License             | https://github.com/FACINGS/collection-manager/blob/main/LICENSE               | GPLv3                                                                       |
| 0b.    | Documentation       | https://github.com/FACINGS/collection-manager/blob/main/README.md             | Overview and "Getting Started"/deployment guide. See links under "Documentation" heading for 6 new docs: (1) User Guide, (2) Plugin System, (3) Contributing, (4) Testing Guide, (5) Data Import Plugin, and (6) Data Types. |
| 0c.    | Testing Guide       | https://github.com/FACINGS/collection-manager/blob/main/docs/testing-guide.md#3-testing-stage-2-milestone-1-deliverables | Documentation for a walkthrough of the UI features. Jump to "3. Testing Stage 2, Milestone 1 deliverables" for a testing guide for Deliverables 1 - 3 in this milestone. |
| 0d.    | Docker              | https://github.com/FACINGS/collection-manager/blob/main/Dockerfile            | Instructions are included in aforementioned "Getting started" guide.        |
| 1.     | TypeScript Implementation | https://github.com/FACINGS/collection-manager                           | Convert all components to TypeScript to improve maintainability/reliability (see Testing Guide for verification) |
| 2.     | UX Improvements     | https://creator.facings.io | (1) Jungle4 EOS testnet support<br />(2) Airdrop - allow minting to multiple accounts<br />(3) Transfers - filter NFTs by name or collection<br />(4) Upgrade navigation / breadcrumbs and small screen optimization<br />(5) IPFS updates - manual address entry, previews, validation, view originals<br />(6) Metadata handling - new social links for collection, better defaults for schema, allow blank immutable fields, improved input validations (see Testing Guide for run-through) |
| 3.     | Plugin Architecture | https://github.com/FACINGS/collection-manager/blob/main/docs/plugins.md       | Design/implement plugin framework to allow for added functionality at the collection level. |

**Additional Information**
The plugin system at this juncture supports collection-level plugins, although the team is working with other developers in the community to design app-level plugins as well. The goal is to make the collection-manager app more extensible for other types of plugins, such as hypothetical analytics and marketplace plugins.