# Designing automated tests for Mule applications

- **Topics**
    - Design unit test suites using MUnit and studio’s related features
    - Identify test requirements and scenarios that are best addressed using integration testing or performance testing
- **Modules**
    
    Module 6
    
- **Module 6: Designing Mule application testing strategies**
    - MuleSoft provided framework and tools for testing, testing strategies, test coverage
    - Architect responsibilities: Build comprehensive test suite of relevant tests for each Mule project to ensure consistent, predictable, and reliable deployments and runtime operations.
    - Types of testing
        - Unit testing - Functionality of a specific unit. External calls or dependencies are mocked
        - Integration testing - All interactions to and from interactive system are functional. Tests the actual messages, request, and/or responses exchanged with external systems.
        - Performance testing - Performance characteristics of the system. Capacity, response time, scalability, reliability, and resource use under various workloads
    - MUnit:
        - Testing tool and framework to test Mule applications. Test and Mule application execute in the same Mule runtime.
        - MUnit and MUnit tools modules. Standard event processors.
        - White-box test cases
        - Manually in Anypoint studio and automatically as part of the Maven-based CI/CD build process
        - Test results and coverage in Anypoint studio or Maven build output
    - MUnit test scopes: All are optional. Behavior, execution, and validation.
    - Mock any processor, define assertions and spy on flow components.
    - Code coverage reports and test tags (unit vs integration tests) on MUnit tests.
    - MUnit test recorder:
        - Reduce the effort of manually creating MUnit tests. Record a specific flow and automatically generate an MUnit test. Records actual input and output events and then uses the input data for test data and output data for assertions.
        - Limitations:
            - You cannot create tests for flows with Mule errors raised inside the flow or already existing in the incoming event, even if an **on error continue** error handler controls them
            - A recorded flow execution ends successfully, but the result does not reach its destination because the application is killed.
            - Your validations fail every time your test runs if you configure spy or assert processors to assert values for random data, time-dependent information (such as timestamps), or values resulting from parallel processes, because those values change in every execution.
            - Mocking values resulting from parallel processes causes a mixture of real and mocked data that compromises the execution of the processors that follow in your test.
            - Although the recorder supports data iteration in the flow, such as recursions or loops, it does not support cases in which the structure of the data being tested changes inside the iteration.
            - The recorder does not support mocking a message before or inside a foreach processor.
            - When using the Test Recorder to generate a test over your flow, you can only mock parameters included in your flow. You cannot mock parameters in sub-flows or in referenced flows through the Test Recorder UI. If you need to mock parameters in sub-flows of any other process in the project, you can modify the mocking component after creating the test.
    - Parameterized MUnit tests: Runs the same tests with different inputs. Test suite configuration >> YAML file parameterization.
    - Integration testing
        - Integration testing: MUnit can also be used as white-box integration testing framework. Assertions, code coverage reports (generated reports), test tags, **do not create MUnit mocks for external dependencies instead create test instances of remote services.** Anypoint platform - Mocking services for APIs. Third-party products - Mockoon, WireMock, Traffic Parrot, DataPower
        - Black-box (functional) integration testing: End-to-end testing. Interact through its published interface. Invoke REST or SOAP web services, Send JMS message, Create files, Insert a records into a database. Observe the application’s response and behavior. Assert that the response and behavior. Have no knowledge of implementation details of the application.  Tools: SoapUI, JMeter, Unified Functional Testing (UFT)
    - Performance testing
        - MuleSoft does not provide particular performance testing tools
        - Plan for performance testing early for applications where performance is critical - JMeter or BlazeMeter
- **Questions**
    - MUnit recorder limitations
    - How to mock for unit testing - MUnit
    - How to mock for integration testing - Mocking services
    - How to mock for performance testing - Mocking services
    - Classify unit test, integration test, user accepted test, and performance test
    - White-box vs black-box testing
    - An organization has strict unit test requirement that mandate every mule application must have an MUnit test suit with a test case defined for each flow and a minimum test coverage of 80%. A developer is building MUnit test suit for a newly developed mule application that sends API request to an external rest API. What is the effective approach for successfully executing the MUnit tests of this new application while still achieving the required test coverage for the MUnit tests? - **Mock the rest API invocation in the MUnits and return a mock response for those invocations**
    - An organization is building out a test suite for their application using MUnit. The integration architect has recommended using Test Recorder in studio to record the processing flows and then configure unit tests based on the captured events? - **Tests for flows cannot be created with Mule errors raised inside the flow or already existing in the incoming event. A recorder flow execution ends successfully, but the result does not reach its destination because the application is killed**
    - Refer to the exhibit. One of the backend systems invoked by an API implementation enforces rate limits on the number of requests a particular client can make. Both the backend system and the API implementation are deployed to several non-production environments in addition to production. Rate limiting of the backend system applies to all non-production environments. The production environment, however, does NOT have any rate limiting. What is the most effective approach to conduct performance tests of the API implementation in a staging (non-production) environment? - **Create a mocking service that replicates the backend system's production performance characteristics Then configure the API implementation to use the mocking service and conduct the performance tests**