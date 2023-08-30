# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** https://github.com/mchosc/eosnf-grant-framework/blob/main/applications/antelopeio_firewall.md
* **Milestone Number:** 1 and 2
* **Milestone Payment Amount:** 27000 USD
* **Contact Name:** John Heeter
* **Contact email:** john@boid.com

## Context
We decided to deliver 2 Milestones at the same time. We've tested everything internally with different scenarios. We are ready for other API providers to start testing the firewall and give us feedback.

## Deliverables
### Milestone 1 — Create Antelope Firewall Prototype
| ID  | Deliverable   | Specification                                                                                                                                                                                                                                                                                                                         |
| --- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0a. | License       | MIT                                                                                                                                                                                                                                                                                                                                   |
| 0b. | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how to configure and run, including technical draft: short document will act as an overview of the technical implementation details as part of the development planning stage. Will guide code structure and development milestones. |
| 0c. | Deployment    | We will provide a Prototype with a limited basic functionalities implemented. For example the firewall will be able to route queries to nodes and return responses with basic blacklisting functionality.                                                                                                                             |

### Milestone 2 — Implement Antelope Firewall MVP version
| ID  | Deliverable           | Specification                                                                                                                                                                                                 |
| --- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0a. | License               | MIT                                                                                                                                                                                                           |
| 0b. | Documentation         | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how to configure and run Alpha and Beta version (MVP).                                                       |
| 0c. | Deployment Alpha      | We will provide a Alpha version with a major features implemented in a basic way. We will begin running on our own nodes. Our goal is to implement blacklisting, round-robin routing and special rules-based transaction handling logic.                                                                                     |
| 0d. | Deployment Beta (MVP) | We will provide a Beta version (MVP) with all features implemented in a basic way. The app should be ready to distribute to external infra providers for feedback and testing of the HTTP RPC functionality. This release will include improvements of functionality implemented in the Alpha. Additionally this release will include statistics and monitoring endpoints for prometheus. Additionally this release will include contract and account prioritization functionality, for example queries for certain contract tables could be rate-limited at a different rate. |

## Additional Information
Code
https://github.com/animuslabs/antelope-firewall
