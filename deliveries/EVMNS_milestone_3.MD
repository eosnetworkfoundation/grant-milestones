# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [EVMNS
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/EVMNS.md)
* **Milestone Number:** 3

**Context:**
For execution of Milestone 3

**Deliverables:**

### Overview of the smart contract's functionalities:

- Domain Registration: Allows users to register unique domain names on EVMNS.
- Domain Management: Enables users to manage their registered domain names, such as changing the domain's profile,
  changing the resolver, modifying TLS certificates, and more.
- Domain Transfer: Allows users to transfer their registered domain names to others.
- Resolver Registration: Allows users to select a resolver to interpret the domain name. Depending on the resolver, the
  domain name can support different functions.
- Domain Resolution: Allows users or third-party dApps to query the profile content of any EVMNS domain name, for
  instance, to check whether an EVMNS domain name is associated with an EVM address.

**Milestone 3 — [EVMNS](https://github.com/evmns/EVMNS)**
Please refer to our public [repo for this project](https://github.com/evmns/EVMNS) for the deliverables set out in the
milestone table below.

- **Estimated duration:** 3 weeks
- **FTE:** 3
- **Costs:** 45,000 USD

| ID  | Deliverable                        | link                                                                                               | Notes                                                                                                                                                                                                                                                                       |
|-----|------------------------------------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0a. | License                            | [License](https://github.com/evmns/EVMNS/blob/main/LICENSE)                                        | MIT                                                                                                                                                                                                                                                                         |
| 0b. | Documentation                      | [Documentation](https://docs.evmns.space/)                                                         | Provide and update documentation for this milestone in the form of instruction files and examples in the repository, provide guidance in the Readme file, and more in-depth guidance in our articles.                                                                       |
| 0c. | Testing Guide                      | [Section in the guide](https://github.com/evmns/evmns-contracts#How-to-run-tests)                  | We will continuously update the usage instructions and testing methods in the docs.                                                                                                                                                                                         |
| 0d. | Docker                             | [Development](https://hub.docker.com/repository/docker/evmns/development/general)                  | Use Docker to start a container that runs a local nodevm instance where specific users and contracts are deployed for developer testing. This ensures that developers have the same environment when using EVMNS.                                                           |
| 1  | Domain Manager                     | [NameWrapper](https://github.com/evmns/evmns-contracts/tree/main/contracts/wrapper)                | The Domain Manager in EVMNS is a domain management contract that allows domain owners to manage the domains they own, change names in the registry and transfer ownership to anyone else.                                                                                   |
| 2  | Reverse Registrar                  | [Reverse Registrar](https://github.com/evmns/evmns-contracts/tree/main/contracts/reverseRegistrar) | The reverse resolver in EVMNS provides the ability to declare reverse records. This is a convenient feature that is commonly used to specify address specification names. It can be used to configure records easily.                                                              |
| 3 | Metadata Storage Management System | [Metadata Query Method](https://docs.evmns.space/dapp-developer-guide/resloving-names/metadata-query-method)                                                                          | Considering data security and real-time performance, the query of metadata is no longer provided through an API. Instead, third-party applications are guided to directly query real-time data within the EVMNS contract on the EOS-EVM to ensure the accuracy of metadata. |
| 4  | Domain Management System           | [Management System](http://13.231.106.101:8098/)                                                   | Build EVMNS domain management system to realize administrators capability of financial review, daily log maintenance review, emergency management, etc. for EVMNS.<br/><br/> Account: observer <br/>Password: 123321                                                        | <br/><br/>                                                                                                                                                                                                        