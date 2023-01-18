# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

- **Application Document:** https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/CETF.md
- **Milestone Number:** 2

**Context**

Main objective of this milestone was to configure and deploy Phase 2 contracts and front-end to the mainnet. 6 msigs were executed to complete the migration. Took us much longer than initially planned because of additional fixes and refactoring of the contracts (wanted to compile contracts using DUNE but run into errors https://github.com/AntelopeIO/DUNE/issues/12). Refactored contracts can be found here: https://github.com/n0umen0n/cetfphase2. Migration was successful, all the features have been tested and are functional. We've also been on-boarding fund managers whose responsibility is to manage the EOSETF. First manager has been whitelisted (gluedog) and there's discussion with Phantom Puppeteer and Trimbot as potential additional managers. 

**Deliverables**

| Number | Deliverable     | Link                                                                                                                                                                                           | Notes                                                                                                                           |
| ------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 0a.    | License         | [LICENCE](https://github.com/n0umen0n/cetfphase2)                                                                                                                                   | MIT                                                                                                                             |
| 0b.    | Documentation   | [DOCS](https://docs.eosetf.io/#/)                                                                                                                                                              | Will be continuously updated.                                                                                                   |
| 0c.    | Unit tests      | [UNIT TESTS](https://docs.eosetf.io/#/)                                                                                                                                                        | Info on tests can be found in the documentation section 2.2.          |
| 1.     | Msigs              | [Msig contract updates](https://bloks.io/transaction/f584be42ebcaf0d62c5ddbc8f5caf5c1f1ff8aa6e6b72b8a382abac45827721e) / [Msig configuration of the fund](https://bloks.io/msig/ironscimitar/config)       
| 2.     | First automatic rebalancing | [First rebalancing of the EOSETF](https://bloks.io/transaction/97c7e069610307c97bd3a3cf43fd76e98f869e049d658f631119f08e2a303495)                                                                                                              
| 3.     | On-boarding fund managers | [Msig](https://bloks.io/transaction/d4da384dff5f52ed280953e120ade2aed880158ef392039254ec1d04309fef94) whitelisting gluedog. We've decided that I and gluedog will conduct next rebalancing. After which next managers will be on-boarded. There is no limit to how many managers can be added.|
