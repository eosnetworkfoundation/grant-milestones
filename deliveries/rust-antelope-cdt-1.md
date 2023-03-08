# Evaluation

- **Status:** In Progress
- **Application Document:** [cost-comparing-research-rust-cdt.md](https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/cost-comparing-research-rust-cdt.md)
- **Milestone:** 1
- **EOS Account:** delightlabs1
- **Previously successfully merged evaluation:** N/A

| Number | Deliverable | Accepted | Link | Evaluation Notes |
| ------ | ----------- | -------- | ---- |----------------- |
| 1. | Research report |<ul><li>[X] EOSVM API analysis</li><li>[X] Antelope code structure research | Within this document |  |

## General Notes

### Report on the feasibility of Rust CDT implementation

### Overview

 This report summarizes research into the feasibility of using the Rust programming language to implement EOS Antelope CDT (Contract Development Toolkit). We analyzed this approach in depth across three key areas.

 The first point is whether EOSVM can run all WebAssembly (WASM) specifications. We believe this could demonstrate the potential of utilizing CosmWasm. Next, we compared CosmWasm and Antelope CDT in order to check which could be improved and which needed more. Finally, we investigated whether Wasmer could be integrated into the core to ensure CosmWasm-Wasmer integration in case CosmWasm does not run on EOSVM.

 In summary, we’ve confirmed that Rust CDT can be built on EOSVM and it also can leverage Cosmwasm to its development. Based on the analysis in this report, we would love to move forward with the development of Rust CDT. We aim to develop Rust CDT on top of EOSVM, but also want to leave room for Wasmer integration in case of unforeseen constraints. The benefits of a Rust-based smart contract platform, including improved security and developer productivity, outweigh the costs of implementation. Rust CDT would provide EOS developers with more options and flexibility, and help EOS remain competitive as blockchain technologies continue to evolve.

### Case 1: The wasm specification coverage in EOSVM

 The known EOSVM restriction is 'no imports other than function'. We first analyzed it and then investigated if there is any unique implementation of specifications and they can affect Rust CDT execution. Our analysis found:

- The restriction with imports does not affect to the Cosmwasm execution on EOSVM as Cosmwasm VM also supports function imports only.
- Value type validation for few instructions in EOSVM also may not necessarily obstruct the implementation. Cosmwasm VM does not support SIMD operation by default, though it can be turned on with an option.

 We believe that Rust CDT can be executed on EOSVM in spite of few constraints like value types in several instructions based on our analysis. Overall, EOSVM provides a feasible environment to execute Rust CDT.

#### No imports other than function

 All imports except for function import has been restricted for guarded pointer in EOSVM. This limitation means that table, mem, and global types could not be imported in EOSVM. Since Wasmer support all imports including function it can be a barrier to utilize Cosmwasm.
 
 Our research concluded that Cosmwasm only supports imports defined in Cosmwasm VM and they consists of functions so it can be executed fully on EOSVM. The code line [(1)](#reference) represents the supported imports in Cosmwasm, which contains functions only.

#### Other unique implementations

 We’ve found that there is one another limit when running WASM on EOSVM, where only number types are allowed in:

- functions’ locals, parameters and returns
- global’s content
- block/if/loop’s returns

 Though Wasmer has not any limit regarding them, Cosmwasm VM disables “allow_feature_simd” option by default so that only single instruction is unable to accept multiple data without setting the option explicitly. The source code for the "allow_feature_simd" option is as follows. [(2)](#reference) [(3)](#reference)

 The reason it was prevented on EOSVM remains unclear but we also delved deeply into quite amount of text formatted WASM file contents from Cosmwasm directly in order to firmly ensure that it does not influence the implementation. The tested Cosmwasm contract source codes are as follows and they all meet the condition for this unique validation.

- https://github.com/CosmWasm/cw-template
- https://github.com/terraswap/terraswap
- https://github.com/CosmWasm/cosmwasm/tree/main/packages/vm/testdata

### Case 2: The comparison between Cosmwasm and Antelope CDT

 In the case that the VM side does not have any constraints for developing a Rust CDT, described in Case 1, the difference between Cosmwasm and Antelope CDT is critical to measure the size of implementation. Here, we compared them in terms of entry point and functionality. Compiler development such as attributes in clang and linker is excluded, which is mandatory.

#### Function formats

- Antelope CDT
  - The name of the function exposed: `apply`
  - Prototype: `func (param i32 i32 i32) (result i32)`
- Cosmwasm
  - The name of the function exposed: `instantiate`, `execute`, `query`, `migrate`
  - Prototype: `func (param i32 i32 i32) (result i32)`

#### Input parameter description

- Antelope CDT
  - With the line [(4)](#reference), the args are encoded or serialized into EOSVM-native type
    - Although it could be uint32_t, uint64_t, etc, we are not sure that the value could be changed into the special standard of EOSVM
- Cosmwasm
  - According to the source code [(5)](#reference)
    ```rust
    fn call_3_args(
        vm_fn: VmFn3Args,
        cache: *mut cache_t,
        checksum: ByteSliceView,
        arg1: ByteSliceView,
        arg2: ByteSliceView,
        arg3: ByteSliceView,
        db: Db,
        api: GoApi,
        querier: GoQuerier,
        gas_limit: u64,
        print_debug: bool,
        gas_used: Option<&mut u64>,
        error_msg: Option<&mut UnmanagedVector>,
    ) -> UnmanagedVector {
        let r = match to_cache(cache) {
            Some(c) => catch_unwind(AssertUnwindSafe(move || {
                do_call_3_args(
                    vm_fn,
                    c,
                    checksum,
                    arg1,
                    arg2,
                    arg3,
                    db,
                    api,
                    querier,
                    gas_limit,
                    print_debug,
                    gas_used,
                )
            }))
            .unwrap_or_else(|err| {
                eprintln!("Panic in do_call_3_args: {:?}", err);
                Err(Error::panic())
            }),
            None => Err(Error::unset_arg(CACHE_ARG)),
        };
        let data = handle_c_error_binary(r, error_msg);
        UnmanagedVector::new(Some(data))
    }
    ```

  - Args 1: Environmental value (block, tx, contract information)
  - Args 2: Information value (message sender, funds)
  - Args 3: Actual method name and its arguments
- In EOSVM, the value encoding could be occurred within EOSVM code

#### Parameter decoding implementation within the contract

- Antelope CDT
  - Deserialization within the contract by EOSVM spec
  - Light implementation and size of the contract
- Cosmwasm based
  - Serialization & deserialization logic from Serde [(6)](#reference)
  - The contract contains Serde logic
  - The contract takes a serialized data and unpack within the contract
  - Adopted near-standard library & heavy size of the contract

#### Where to modify that Cosmwasm contracts could be compatible on Antelope

Despite the contract system in Antelope is sophisticated, the number of developers and users are being flocked to the Cosmwasm-based contracts [(7)](#reference) and they become treated as a standard in WASM-based contracts.

- Support to trigger more exported method on Leap code
- Using Serde C++ implementation library [(8)](#reference), serialize the args on Leap and disable ABI creation
- Do not handle the input data within VM, but bypass it into the contract
- Organize the environmental data & message data and provide them into the contract

### Case 3: Wasmer integration on Antelope Leap

#### Abstraction & current implementation check

- Connection between Antelope Leap <> VM
  - Related part
    - VM connection interface in Leap
      - runtime_interface.hpp [(9)](#reference)
      - The implementation is located in runtimes [(10)](#reference)
    - VM backend
      - EOS VM provides the backend APIs so that consumers don’t need to know how the VM is actually working
      - backend.hpp [(11)](#reference)
  - Description of each interface
    - `instantiate_module()`
      - Create a context with guaranteeing the distinct pointer by each context
      - Without this method, the pointer could be shared with other context and it could affect to the other result of the execution
    - `fast_shutdown()`
      - Clean all state dependent parts and disconnects from the VM
    - `immediately_exit_currently_running_module()`
      - Throw proper exception by VM
    - `apply()`
      - Load the proper WASM binary and its related context (table, account, etc)
      - Implement a light profiler that measures execution time and CPU time
      - Execute the exported method `apply()` of the contract with given args
      - As WASM binary input/output is handled from Antelope Leap, so there’s no need to convert in VM runtime
        - Overall, the main interface to focus is `apply()`
- More essential implementation
  - Profiler
    - Antelope defines execution time and CPU time as their resource. The amount is set by how much the user stakes, and the execution should be ceased immediately if the execution exceeds the resource the user has.
    - By these reasons, profiling logic should be developed.
    - While EOSVM was designed with awareness of this demand, Wasmer does not contain the feature yet. So, additional profiling logic is needed on it
    - As general profiler consumes a lot of system resource, it is recommended to build from the scratch.
  - Validation
    - Before store(`setcode`) & execution, Antelope core checks whether the WASM binary is proper or not.
    - Checking criteria
      - Does `apply()` implement?
      - Does all essential host functions are imported properly?
      - Is `apply()` exported? (set as public method)
      - Does `apply()` implement as proper type (3 `i32` types args, 1 `i32` output)

#### Brief implementation strategy

- Backend
  - Based on the interface of EOSVM backend endpoint, implement the backend wrapping Wasmer
  - In Antelope → VM calling part, do not call via Wasmer API itself but call the backend API above for unifying the way of the implementation.
  - `initialize()`
    - Wasmer C API is prepared. But not yet for C++. `extern "C"` is required
    - C API [(12)](#reference)
    - Snippet: Connecting engine process

      ```cpp
      extern "C" {
          #include "wasm.h"

          wasm_engine_t* engine = wasm_engine_new();
      }
      ```

    - Snippet: State initialization

      ```cpp
      extern "C" {
          #include "wasm.h"

          wasm_store_t* store = wasm_store_new(engine);
      }
        ```

    - Some restriction from `extern "C"`  is concerned
  - `execute()`
    - Contract binary is shipped on `ctx` object
    - Snippet: Could be useful in the context loading step

        ```cpp
        std::cout << "Loading binary..." << std::endl;
        std::ifstream file("hello.wasm");
        file.seekg(0, std::ios_base::end);
        auto file_size = file.tellg();
        file.seekg(0);
        auto binary = wasm::vec<byte_t>::make_uninitialized(file_size);
        file.read(binary.get(), file_size);
        file.close();
        if (file.fail()) {
          std::cout << "> Error loading module!" << std::endl;
          exit(1);
        }
        ```

- VM connection part on Antelope Leap
  - `instantiate_module()`
    - Guaranteeing the uniqueness of the pointer seems to be reusable
    - In `init` of the backend, replace into to backend of Wasmer wrapper
  - `fast_shutdown()`
    - In case of EOSVM, it clears the result of the profile
    - No implementation in WAVM
    - The action could be clearing profile, similar to EOSVM case
  - `immediately_exit_currently_running_module()`
    - Throw any proper exception
  - `apply()`
    - Contract upload
      - In Leap core, check the account name of the contract and its action name. Take `if` clause and resolve within the Leap core.
      - Don’t need to implement in Antelope Leap <> VM
    - Contract execution
      - Implement the execution part on the Leap core for the binary itself should be loaded on the context from the Leap core state DB.
      - Wrap the result from the Wasmer execution into the context object. And make it consume on Tx side.
- Not exist on Runtime interface but should be developed
  - `void indicate_shutting_down();`
    - Marking as shutdown
  - `static void validate()`
    - Required in order to implement module checking and `apply()` method existence.
    - Implementation on the core is simple but it should be well built on the backend side.
- Any addition point
  - In `libraries/chain/include/eosio/chain/wasm_interface_private.hpp`, `wasm_interface_impl` , add one more `if` clause like `#ifdef EOSIO_EOS_VM_RUNTIME_ENABLED` for the new VM
  - More point to add `ifdef` clause
    - wasm_interface.cpp
    - wasm_interface_private.hpp
    - chain_plugin.cpp
  - Some `if` s

    ```cpp
    enum class vm_type {
    	eos_vm,
    	eos_vm_jit,
    	eos_vm_oc
    // add one
    };
    
    //return string description of vm_type
    static std::string vm_type_string(vm_type vmtype) {
       switch (vmtype) {
       case vm_type::eos_vm:
          return "eos-vm";

       // case add_one_more
       //   return "wasmer";

       case vm_type::eos_vm_oc:
          return "eos-vm-oc";
       default:
           return "eos-vm-jit";
       }
    }
    
    ...
    
    std::istream& operator>>(std::istream& in, wasm_interface::vm_type& runtime) {
       std::string s;
       in >> s;
       if (s == "eos-vm")
          runtime = eosio::chain::wasm_interface::vm_type::eos_vm;
       else if (s == "eos-vm-jit")
          runtime = eosio::chain::wasm_interface::vm_type::eos_vm_jit;
       else if (s == "eos-vm-oc")
          runtime = eosio::chain::wasm_interface::vm_type::eos_vm_oc;
       // here
       else
          in.setstate(std::ios_base::failbit);
       return in;
    }
    ```

### Conclusion & Cost Estimation

#### Solution

- Based on the current EOSVM, we recommend integration of Cosmwasm-based contract system.
- If there is a lack of resources to maintain the EOSVM, integrating with Wasmer would be an option.

#### Cost

In the case of enabling CosmWasm-based contracts, the estimated cost is approximately **USD 225K**. This cost includes:

- Development and Testing: USD 180K
  - Antelope core side
  - EOSVM modification
  - Contract SDK
- Documentation: USD 20K
- Project management: USD 25K

The timeline is approximately 3 months for development and 2 months for testing and documentation.

In addition, we estimated **USD 40K / yr** for the repository maintenance. This budget would continue before the community’s active contribution, or technical follow-up for other maintenance entity.

### Appendix: Implement Rust CDT following current Antelope CDT

Additionally, we analyzed the existing implementation [(13)](#reference) to understand what more is needed for our subsequent development.

The existing Rust CDT project provides a familiar experience for C++ contract developers since it serves quite a similar format to the current C++ CDT. However, there are some points which we can enhance:

- `wasm32-unknown-unknown` is more recommended rather than the current target `wasm32-wasi` for safety, especially automatically blocks system access
- More maintainers, better stability
- Manual implementation in codegen may draw difficulty to track and not a general way to compile contract source code, which can deviate from WebAssembly standards [(14)](#reference)
- A lack of support for a few `eosio` attributes (e.g. `eosio::read_only`) required
- Integration testing framework and mock VM testing, requiring a fully running chain for testing
- Few advanced features from CosmWasm SDK. To further explain the reason that the CosmWasm SDK may be a better option:
  - Is becoming an industry standard
  - Is regularly maintained and adopts the latest technologies quickly
  - Has no ABI and is easy to organize message formats, though larger contract sizes, which is developer-friendly
  - Can adopt many pre-written contract examples from other Cosmwasm contract repositories

### Reference
1. https://github.com/CosmWasm/cosmwasm/blob/main/packages/vm/src/compatibility.rs#L12
2. https://github.com/CosmWasm/cosmwasm/blob/main/packages/vm/src/wasm_backend/gatekeeper.rs#L64
3. https://github.com/CosmWasm/cosmwasm/blob/main/packages/vm/src/wasm_backend/gatekeeper.rs#L498
4. https://github.com/AntelopeIO/eos-vm/blob/main/include/eosio/vm/execution_context.hpp#L287
5. https://github.com/CosmWasm/wasmvm/blob/main/libwasmvm/src/calls.rs#L488-L528
6. https://serde.rs
7. https://medium.com/electric-capital/electric-capital-developer-report-2021-f37874efea6d
8. https://github.com/injae/serdepp
9. https://github.com/AntelopeIO/leap/blob/main/libraries/chain/include/eosio/chain/webassembly/runtime_interface.hpp
10. https://github.com/AntelopeIO/leap/tree/main/libraries/chain/webassembly/runtimes
11. https://github.com/AntelopeIO/eos-vm/blob/main/include/eosio/vm/backend.hpp
12. https://github.com/WebAssembly/wasm-c-api/blob/main/include/wasm.h
13. https://github.com/uuosio/rscdk
14. https://github.com/uuosio/rscdk/blob/main/crates/codegen/src/contract.rs