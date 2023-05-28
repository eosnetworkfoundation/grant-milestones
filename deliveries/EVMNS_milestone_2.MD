# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**

* **Application Document:** [EVMNS
  ](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/EVMNS.md)
* **Milestone Number:** 2

**Context:**
For execution of Milestone 2

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

**Milestone 2 — [EVMNS](https://github.com/evmns/EVMNS)**
Please refer to our public [repo for this proejct](https://github.com/evmns/EVMNS) for the deliverables set out in the
milestone table below.

- **Estimated duration:** 4 weeks
- **FTE:** 5
- **Costs:** 100,000 USD

| ID  | Deliverable          | link                                                                                 | Notes                                                                                                                                                                                                                                                                                          |
|-----|----------------------|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0a. | License              | [License](https://github.com/evmns/EVMNS/blob/main/LICENSE)                          | MIT                                                                                                                                                                                                                                                                                            |
| 0b. | Documentation        | [Documentation](https://docs.evmns.space/)                                           | Provide and update documentation for this milestone in the form of instruction files and examples in the repository, provide guidance in the Readme file, and more in-depth guidance in our articles.                                                                                          |
| 0c. | Testing Guide        | [selection in the guide](https://github.com/evmns/evmns-contracts#How-to-run-tests)  | We will continuously update the usage instructions and testing methods in the docs.                                                                                                                                                                                                            |
| 0d. | Docker               | [Development](https://hub.docker.com/repository/docker/evmns/development/general)    | Use Docker to start a container that runs a local nodevm instance where specific users and contracts are deployed for developer testing. This ensures that developers have the same environment when using EVMNS.                                                                              |
| 1   | Core Contracts       | [Registry](https://github.com/evmns/evmns-contracts/tree/main/contracts/registry)    | At the core of EVMNS is a smart contract that maintains a list of all domains and sub-domains and stores three key pieces of information about each domain: the owner of the domain, the resolver of the domain, and the cached time to live (i.e., TTL) for all records under the domain.     |
| 2   | Domain registrar     | [Registrar](https://github.com/evmns/evmns-contracts/tree/main/contracts/evmregistrar) | EVMNS allows domain owners to manage all their domains, including sub-domain registrations. We will provide standard domain registration contracts and interfaces, allowing all compliant contracts to access and renew, transfer and other operations for domains.                            |
| 3   | Root Node Management | [Root](https://github.com/evmns/evmns-contracts/tree/main/contracts/root)            | Completing the design of the root node, EVMNS will lock the control of the root node so that the root owner cannot influence the ownership of the .evm domain and set the root node to be held jointly by the community in a multi-signature contract, guaranteeing all the power of the user. |
| 4   | Domain Resolver      | [Resolver](https://github.com/evmns/evmns-contracts/tree/main/contracts/resolvers)   | Resolvers are responsible for the actual process of translating names into addresses. Any contract that implements the relevant standards may act as a resolver in EVMNS.                                                                                                                      |<br/><br/>