# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** [genereos-testing-libraries
](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/genereos-testing-libraries.md)
* **Milestone Number:** 1

**Context:**
For execution of Milestone 1

**Deliverables:**


 **Milestone 1 — [Smart Contract Testing library](https://github.com/GenerEOS/Qtest)**

Please refer to our public [repo for this proejct](https://github.com/GenerEOS/Qtest) for the deliverables set out in the milestone table below.
- **Estimated duration:** 1 month effort and 2 months total delivery duration including testing and documentation
- **FTE:**  4
- **Costs:** $40500 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | We will provide both inline documentation of the code and a basic tutorial and operating instructions that explains; Setup of a testing environment; Config and write contract-tests; API reference |
| 0c. | Testing Guide | NA - the testing guide will be included in the documentation as the library is testing in nature. |
| 0d. | Docker | NA - included on deliverable 1 |
| 0e. | Article | We will publish an article that explains the work completed with the content geared towards our target audience of developers and entrepreneurs in the EOS and EOSIO ecosystem.
| 1. | Dockerize a light EOSIO node that can be run on the users system automatically. With several options on initial chain state for different chains e.g. EOS/TELOS/WAX | Dockerfile to setup each chain; shell script to initialize smart contract/data; docker image stored in docker hub |  
| 2. | Provide all core functionalities for unit-test| Javascript API to interact with the docker container within the testing scripts; Javascript Core APIs for developer to interact with chain for example: set contract, push action, get table and an array of wrapped functions that allow developers to quickly interact with blockchain; Assertion library for smart contract testing|  
| 3. | Provide some advanced functionalities | Nodejs modules and docker shell scripts to manipulate blockchain state and time for special testing purposes e.g. booting the chain with an arbitrary time; Init/reset smart contract table data with minimal modification of smart contract; Functionalities to test accounts/permission|  **Additional Information**


> This project initially had 3 miletones but based on feedback on the inital proposal it was condensed to 1 milestone. Therefore, this project is now at completion. 
