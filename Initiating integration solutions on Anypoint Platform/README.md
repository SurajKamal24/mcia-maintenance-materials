# Initiating integration solutions on Anypoint Platform

- **Topics**
    - Summarize the fundamental value proposition of MuleSoft catalyst and catalyst knowledge hub
    - Differentiate between functional and non-functional requirements for integration solutions
    - Select features of Anypoint Platform for designing and managing web and event-driven APIs
    - Select deployment options of the Anypoint platform control plane and runtime plane
- **Modules**
    
    Module 1, Module 2, Module 3, and Module 7
    
- **Module 1: Introducing integration solutions architecture**
    - Goals: Business outcomes + Technology delivery + Organization enablement = Customer success
    - Objectives of enterprise integration solutions:
        - Address in-scope requirements of stakeholders related to the integration scenarios and use cases.
        - Document different views to address these goals and concerns.
        - Additional documentation may be required to align stakeholders from different business units or job roles
    - Integration solution architecture vs enterprise architecture
        
        Integration solution architecture
        
        - Builds a technology blueprint that guides the integrations of enterprise applications
        - Documents individual integration solutions
            - For example, message-based integration, batch processing, and ETL
            - Often in the form of direct integration between two systems
        
        Enterprise architecture
        
        - Defines a blueprint of the structure and operations of an organization to effectively achieve its current and future objectives
        - Provides standards and frameworks to guide individual solution architecture
        - Continually builds up an organization’s application network
    - Aspects of MuleSoft catalyst approach. Catalyst has six playbooks to guide best practices
        - Business outcomes - Business outcomes - Define outcomes with clear KPIs and align stakeholders.
        - Technology delivery - Anypoint Platform, projects - Get up and running with Anypoint Platform and start building APIs and integrations.
        - Organization enablement - Center for enablement, internal support, and training - Ensure your organization is ready to use and adopt the Anypoint Platform
    
    ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled.png)
    
    - Catalyst knowledge hub → Playbooks and their relation → Available assets, knowledge hub structure & feedback model → MuleSoft catalyst GitHub repository
    - Types of documentation in an integration solution architecture
        - Requirements - Functional requirements (FRs), non-functional requirements (NFRs), service-level agreements (SLAs). NFRs must carefully specify criteria and tolerances. For example: “All data at rest must be encrypted per corporate standards”
        - Architecture - Views of systems and subsystems, views of interactions, logical data model, security, and operations etc.
        - Risk, dependencies, and references
    - Documenting requirements
        - User stories are often used in Agile development, and they have a specific format. They are placeholders that are used to start conversations about requirements
        - Use cases are another option, but they do not have a specific format
    - Discovering requirements
        - Functional requirements are often discovered from user stories. Triggering events, acceptance criteria or other expected outcomes, and expected errors and error handling
        - Non-functional requirements (quality attributes) may exist beyond of a user story.
            - May be invented by industry or other external authorities
            - Place constraints on functional requirements
                - Single sign-on is centrally supported by the enterprise LDAP server
                - The system must survive Mule runtime restarts
                - If the system is offline for 30 seconds, a status page must appear. Requires defining failure, uptime, downtime, and time between failures
    - Identity and document interactions
        - Details of all the interactions between systems and stakeholders must be defined in each use case or user story
        - Must specify the details of most important use cases and user stories first to work efficiently
        - Standard templates and best practices should be agreed upon and used for architecture documents
    - Modeling notations for architecture
        - Architectures are documented with various diagram notations, languages, and tools, such as
            - UML, ArchiMate 3, FMC, isometric topology, BPMN 2.0 etc.
            - Free-form (e.g., flow charts, box and line drawings), whiteboards photos, etc.
        - Choice vary by organization and project
    - Identify architecture documentation requirements.
        - Review an example architecture template from MuleSoft catalyst knowledge hub
        - Critique the example architecture template. Functional and non-functional requirements
    - Summary
        - MuleSoft uses catalyst to deliver integration solutions, focusing on three areas that are necessary for successful outcomes. Business outcomes, technology delivery, and organization enablement.
        - Integration solutions involve linking together different software applications to act as a coordinated value.
        - Diagram notations, languages, and tools vary by organization.
- **Module 2: Identifying Anypoint Platform components and capabilities**
    - Anypoint Platform: A unified, highly productive, and hybrid integration platform that creates a seamless distributed system of apps, data, and devices. Manages full API lifecycles to promote API-led development.
    - One common runtime for all types of deployments. On-premises & private cloud, hybrid, hosted by MuleSoft, cloud service providers like AWS, Azure, and Pivotal cloud foundry
    - Design once, deploy anywhere
    - Control plane and runtime plane within the context of Anypoint Platform
        - Control plane: The components of Anypoint Platform that are involved in the design, development, and management of APIs and Mule applications
            - Anypoint design center: Flow designer, API designer, and visual API designer
            - Anypoint exchange: Exchange portal
            - Anypoint management center: Runtime manager, API manager, Access management, and Analytics
        - Runtime plane: The components of Anypoint Platform where the APIs and Mule applications are deployed
            - Mule runtime engine, Anypoint connectors, and runtime services
    - Mule application: A Mule application consists of code and related files, and it runs in a Mule runtime. Deployed or packaged as JAR, triggered by internal or external events, and processes each event through event processors and connector operations
    - Mule runtime engine: Mule applications are deployed to a Mule runtime. A lightweight, Java-based integration platform or application server. Provisioning options: CloudHub, Runtime fabric on OpenShift, Runtime fabric on self-managed Kubernetes, Runtime fabric on VMs/Bare metal, and customer-hosted. Studio comes with an embedded Mule runtime for local development.
    - Mule applications accept and process events (which are created via an event source) through a series of event processors that are linked together in one or more flows. A flow is a linked sequence of event processors. Must have at least one event processor. Can be invoked by a flow reference. Error handling and event source are optional
    - Event source: Creates Mule 4 events at the start of a flow. A flow can start with an event source. Event source accepts inbound events and converts them to Mule events. The Mule event is passed or copied between event processors in the flow
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%201.png)
        
    - API-led connectivity is a style of integration architecture that priorities APIs and assigns them to one of three tiers: System APIs, Process APIs, or Experience APIs. Access every component or system through its published interface - Typically, web APIs through a RESTful, HTTP based interfaces. Define a machine-readable contract for this interface - Using OpenAPI or RAML specifications. Treat the interface as a product in its own right - Versioned with defined stakeholders.
    - Anypoint Platform components used to create and manage web APIs. A unified platform to design, build, test, share, and manage APIs.
        - Design: Design center, and Anypoint studio
        - Simulate: API console
        - Feedback: API portal, and exchange
        - Validate: API notebook
    - API led approach: At first, component interfaces can be designed with API specifications that are easier for less technical stakeholders to understand. Write, publish and version APIs in Anypoint design center. Share, mock, test, and reuse APIs with Anypoint exchange. Test and mock APIs in Anypoint exchange using an API portal and its API console UI. Encourages visibility and early agreement by less technical stakeholders.
    - Advantages of developing with published APIs. Business validations and field constraints are specified in the API. Developers do not need to code these validation checks or error types speeding up API implementation and development. APIs encourage early testing and self-discovery. API clients can be tested and “fail fast” before API implementations are created. Promotes parallel development and self-discovery of existing services and other reusable assets. Complex business objects and constraints are specified and agreed upon in the API specifications.
    - REST API specification options
        - Open API specification (OAS): Formally called Swagger. Another open standard to define REST interfaces in YAML or JSON format
        - REST API Modeling Language (RAML): A standard invented by MuleSoft. Based on YAML (YAML Ain’t Markup Language)
        - Standard characteristics: Language agnostic to easily model XML, JSON in a more readable syntax. Readable by less technical, more business-focused staff. Support tools to autogenerate scaffolded implementations
    - Designing web APIs using API designer. Using the visual editor in API designer helps to quickly build valid REST API specifications. Automatically writes the correct key names, indentation, etc. Guides you through all required and optional steps. You can switch to the manual code editor later, but then you cannot go back to the visual editor.
    - Walkthrough 2-1: Create a REST API using API designer. Define a simple API specification using the guided visual editor. Define type and value constraints on request and response parameter values. Flip between RAML and OAS. Edit the RAML to transition to the API designer.
    - Testing an API with API console. API console is a visual REST client that can be accessed in a web browser. API console is embedded in various Anypoint platform components.
        - API designer: So the API designer can test the current API’s example data
        - API portals in Exchange: So the API users and developers can try out the selected API version
        - Anypoint studio in the API design perspective: So the developers implementing the API can test the current API’s example data
        - Mule API implementation that use APIkit: To test the actual deployed API implementation
    - Mocking an API for REST clients
        - You can mock an API before it is implemented. Useful for early feedback from developers, and for parallel development of API clients and API implementation. Available in API designer and Anypoint exchange.
        - Use the mocking service to run a live simulation. Returns a sample API responses defined in the API definition. Allows for the addition of behavioral headers for more mocking use cases (errors, injecting delays, selecting specific examples as response). Can be made public - Set an expiration date for the public URL (optional).
    - Walkthrough 2-2: Test and mock a REST API using API designer. Mock a REST API specification so it can be tested by other REST clients. Invoke the mocking endpoint with MS2-* behavioral headers. [Add Behavioral Headers to Simulated API Calls | MuleSoft Documentation](https://docs.mulesoft.com/design-center/apid-behavioral-headers)
    - Share API specifications using Anypoint Exchange. REST APIs can be published to Anypoint Exchange from API Designer or Anypoint Studio, or they can be uploaded as a ZIP archive. API designer can import REST APIs from Anypoint exchange. Anypoint studio can import REST APIs from Anypoint exchange. Autogenerates scaffolding for API implementation using APIkit. Allows for edits and updates to the API specifications. Different versions can be imported and exported.
    - Walkthrough 2-3: Share API specifications using Anypoint exchange. Publish an API specification defined in API designer to Anypoint exchange. Document the API in Exchange including category and tags. Save search for the organization.
    - Event-driven API (AsyncAPI) support in Anypoint Platform. Event-driven APIs are supported in Anypoint Platform through the AsyncAPI specification. Anypoint Platform provides tools to design, publish and discover event-driven APIs (AsyncAPI documents).
    - AsyncAPI: YAML based language used to describe and document event-driven APIs in a machine-readable and human-readable format. Open-source and protocol agnostic. Describes the vent-driven API using four main concepts. Message: Payload and optional headers exchanged with other services. Channel: Destination to send or receive message. Methods: PUBLISH, SUBSCRIBE. Protocol and server: Technology to transport messages. AsyncAPI document: An event-driven API specification expressed in AsyncAPI.
    - Sample AsyncAPI specification.
    - Design event-driven APIs using API designer. Craft event-driven APIs with AsyncAPI. Reuse RAML datatypes for AsyncAPI schema definitions. Render high-quality documentation.
    - Universal API management on Anypoint platform. Open and flexible platform for any API, deployed anywhere. Accelerate application delivery, implement any architecture, and operate in any environment.
    - Full life cycle API management for any architecture and environment. Anypoint Mule gateway for APIs running on CloudHub, RTF, or Mule runtimes. Anypoint service mesh for microservice environments with Istio. Anypoint flex gateway for microservice, container, and stand alone gateway environments without Istio.
    - Anypoint flex gateway is an ultrafast API gateway designed to manage and secure APIs running anywhere.
        - Performance: Build response experiences. Modern ultrafast API gateway with small memory footprint and high throughput allowing greater API density. Install in minutes with containers and declarative configuration files. Real-time reload of configuration and policy changes ensuring zero downtime with no lag in serving customer requests.
        - Openness: Extend Anypoint to all APIs. Manage any service across any environment or architecture-microservices to monolith-with a gateway that can be deployed anywhere. Native fluent bit support for easy output of logs to third party systems. Support for Kubernetes, docker containers, and VM/Cloud instances running Linux.
        - Security: Secure any API running anywhere. DevOps friendly through automated CI/CD deployments using declarative configuration files. Robust set of authentication, security, quality of service, and traffic management policies. Zero trust security by default no API access until explicitly given.
        - Flexible control through local and connected modes. Control Anypoint flex gateway configuration from Anypoint platform in connected mode. Configure gateways using the CI/CD pipelines in local mode.
    - Configure Anypoint flex gateway in connected mode. Deploy and run flex gateway as a Linux service, docker container, and Kubernetes ingress controller. Register with Anypoint platform. Add APIs to flex gateway from API manager and apply policies
    - Managing Anypoint flex gateway in local mode. Declarative configuration file defines API instances and other configurations such as logging (Inline and resource-based). Flex gateway automatically refreshes when configuration files change.
    - Comparing the MuleSoft API gateways’ capabilities
    
    |  | Anypoint Mule Gateway | Anypoint Service Mesh | Anypoint Flex Gateway |
    | --- | --- | --- | --- |
    | Architecture Pattern | API running on MuleSoft (CloudHub), RTF, or Mule runtime | Microservice environment with Istio | Microservice, container, and stand alone gateway environment without Istio |
    | Use cases | Traditional Mule applications & integrations | Customer has adopted Istio as a service Mesh microservices strategy | Stand alone gateway, distributed microservices, or polyglot integration ecosystem - without Istio |
    | IT user | MuleSoft Developer | Kubernetes administrator | Any developer |
    - Anypoint Mule gateway capabilities. Mule runtime includes an embedded API gateway. Separates orchestrations. Leverages governance capabilities. Apply policies on top of a Mule application without having to write any code.
    - API manager can define and manage API policies for registered Mule applications. Mule applications can have governance offloaded from code in Mule application to configuration via API manager. API policies are configured on an instance in API manager. API policies are then automatically downloaded and enforced in Mule applications. API manager can autogenerate API proxy applications for API implementations based on a corresponding OAS or RAML API specification. Even for REST implementations that are not Mule applications. The API proxy applications can be deployed to Runtime fabric, CloudHub or customer-hosted mule runtimes.
    - API Autodiscovery: The Autodiscovery configuration connects a Mule application with an API manager account. Offloads API governance and policies from the API implementation (the Mule application) to a centralized management plane used by runtime admins, not developers. Simplifies non-functional requirements for Mule application developers so they can focus on desired business data transformations and integrations.
    - Components used to implement Mule applications: Both Anypoint low designer and Anypoint studio create Mule applications. Anypoint studio provides more advanced capabilities compared with Flow designer. Under the hood, Mule applications are Java applications that are configured by Mule applications XML files.
    - Anypoint platform deployment options:
    
    ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%202.png)
    
    - Summary: Anypoint Platform, Full API lifecycles to promote API-led development, Anypoint exchange as central repository, Flow designer or Anypoint studio, Mule runtimes, MuleSoft-hosted in the cloud (CloudHub) or customer-hosted (in the cloud or on-premises), API manager, Runtime manager.
- **Module 3: Designing integration solutions using Mule applications**
    - How Mule 4 events progress through event processors in a Mule application. Flows always function synchronously. Each event processor outputs a Mule event. Some connector operations (such as async) copy the Mule event for concurrent processing (on a new thread). To call event processors asynchronously, for concurrent processing, wrap them in an async scope.
    - Flows vs sub flows. Flow: Regular flow. Private flow - Only called within the application via flow reference, API Kit router, or a DataWeave lookup function. Sub flow: No event source. No error handling (uses whatever the caller defines).
    - Anypoint connectors. Abstract and simply connections to third-party resources and other protocols. Connectors are connected modules. Mule SDK - building custom modules. REST connect - Generated automatically for a REST API at publish time by Anypoint exchange.  Both connectors and modules are built using the Mule SDK (Java or XML). Connectors are divided into various categories based on support and distribution rights.
    - Invoking REST or SOAP services. An Anypoint HTTP or Web service consumer connector. Custom connector can explicitly expose the operations of the web service and simplify some operations, such as authorization and authentication. REST connect faster than HTTP connector.
    - Advantages of using Anypoint connectors. Facilitate integration of Mule applications with third-party systems. Do not require you to study and code to underlying protocol or security. Speed up development. Easier to maintain. Anypoint studio connection to Anypoint platform to find and install connectors or modules
    - Using an API-led development approach. Using API specification which are more human readable than Mule application code. Focus on business data and operations. MuleSoft supports two web API standards: OAS and RAML. RAML is more human readable compared with OAS. Anypoint exchange has the ability to convert to and from both of these formats.
    - Designing and sharing APIs with Anypoint platform. Design center, test API behavior in the visual API console and mocking service. Anypoint studio, author new & edit, automatically synchronize them with design center.
    - Exchange, publish API specifications, encourages reuse & collaboration, available for both API implementers and API consumers. API portal: Make REST requests to an actual web API implementation URL or a mocking service. Interact before the API implementation is complete. Allow client development in parallel. Automatically convert between OAS and RAML. REST connect for Mule 3 and Mule 4.
    - APIkit: Autogenerates scaffolding for Mule flows. Validate request data, creates response and errors. Returns example responses. Data validation fail fast for invalid inputs without additional custom coding or validation. Also generates an API console. API console is accessible via a flow embedded in the scaffolded API implementation. Allows adhoc testing, avoid need for REST client, and provides a UI and docs from the REST API specification. Can be disabled if not needed
    - Walkthrough 3-1: Implement APIs using APIkit.
    - API-led development simplifies the interface between clients (consumers) and providers. REST connectors. hides complex details of the backend endpoints. Same REST API specifications to promote parallel development. Both clients and providers can share experiences and best practices.
    - REST connect: Reflect the RESTful API with operations per methods per resource. Shield developers from manually defining parameters, fail fast to quickly identify issues, define specific metadata to help with data transformations, if invalid parameters or data is input to the connector, specific context-sensitive error messages are generated, and track asset version via dependency,
    - Walkthrough 3-2: Call a REST API from a Mule application using a REST connect connector.
    - Reflecting questions: Considering APIkit - How do you extend the skeleton? What role can API console play in testing? Considering the REST connect connector - Why would you use an HTTP request instead of a REST connector? How is a REST connector different from APIkit? How does an APIkit and a REST connector impact the API lifecycle?
    - Sharing connections and other configurations. Global elements hold a named set of configuration parameters. E.g., database connection configuration shared by database operations. Change once, applies to all.
    - Mule domains can share global elements across mule application on the same runtime. Global configuration elements can be added to a Mule domain project. One or more Mule applications can be associated with the same Mule domain. A Mule domain is deployed to a Mule runtime before deploying the apps. Mule applications linked to the Mule domain can share its configuration. Mule domains are not supported in CloudHub nor in Runtime fabric. Single application per Mule runtime means not applicable.
    - Class-loading lifecycle of Mule 4 modules: Each Mule 4 module has an independent and isolated class-loading lifecycle. Supported by a sophisticated hierarchy of class loaders. Mechanism to isolate Java classes and libraries used by different modules. Allows conflicting versions of Java libraries (with potentially the same classes and interfaces) to be used by different modules in a Mule application without conflicts.
    - Mule 4 class-loading isolation: Mule 4 uses separate class loaders to isolate the Mule runtime, Mule applications, and modules from each other. Each class loader specifies the packages (rather than classes and resources) to export as part of the module’s interface. Applications descriptor - mule-artifact.json
    - Isolating classpaths for different components in Mule 4.
        - Artifact class loader - A regular Java class loader pointing to the JAR files included in the extension. This class loader will load all files and classes of the extension.
        - Artifact filtering class loader - A wrapper created over the artifact class loader, which enforces the access restrictions to the extension code for foreign artifacts (the app or other plugins). It uses the content of the mule-artifact.json descriptor to determine what is public.
        - Extension code - The Mule extension code. Uses the artifact class loader (which does not have any restriction) and is only able to locate resources of the plugin itself.
        - Application code - Mule app. Uses the artifact filtering class loader of the module to prevent the app from accessing restricted code or resources
    - Common Mule 4 connectors. Anypoint studio ships with some common connectors. New connectors downloaded from Anypoint exchange.
    - Mule HTTP connector - Both client and server operations. HTTP 1.0 and 1.1 are supported (HTTP 2.0 is not supported). Basic security filter, listener, load static resource, and request. The Mule HTTP connector uses project Grizzly libraries internally. Grizzly is a standard open source library supporting the HTTPS protocols. Uses selector thread pools. Selector threads check the state of the NIO channels and create and dispatch events when they arrive. Listener selectors poll only for request events. Requester selectors poll only for response events. HTTP listener has a shared selector pool for all Mule applications deployed to a particular Mule runtime. HTTP requester has a dedicated selector pool for each Mule application.
    - Database connectors - Can all out to almost any JDBC relational databases. Any database engine for which you have a JDBC driver. Support for DDL, DML, Stored procedure, DB script, Bulk operations, On table row event source.
    - File and FTP/FTPS/SFTP connectors - All have the same set of operations and they behave almost identically. Support for - File matching and watermarks. Overwriting, appending, and generating new files, creating and listing directories.
    - SaaS connectors - Dedicated connectors for SaaS systems, support specialized and optimized operations.
    - Salesforce connector event processing model - Salesforce applications send events (or notifications) that Mule applications consume to take further action. Publishers and subscribers communicate with each other through events. One or more subscribers can listen to the same event and carry out actions. The salesforce connector supports event processing by subscribing to a topic.
    - Thru managed file transfer processing model - Thru MFT is a MuleSoft-certified third-party connector. Free with a Mule EE subscription (Note: OptiPaaS license costs are separate). Download from Anypoint Exchange. Provides file management via Thru’s OptiPaaS file management server. Provides audits, alerts, and replay for file transfers. Includes processing dashboards to monitor and control all file transfers. Thru OptiPaaS (MFTaaS) is the post office where partners and the enterprise set up their endpoints to send and receive files for each process. The same endpoints can be used in multiple processes and hence are referred to as reusable endpoints. The process uses a connector (Thru MFT connector for MuleSoft, in this example) to pick up files and possibly drop off files with the delivery instructions. The post office places files for a specific process in a single pickup box. This means the consuming process (the flow) is decoupled from file sources and does not change when file source change. The platform takes the files from the Drop-off box and delivers them to the targets via the organization endpoints.
    - Mule SDK - Building custom connectors in Mule 4. Choose OOTB over custom connectors. Evaluate if it is worth creating a customer connector.
    - Mule XML SDK - Alternative to the more advanced Java-based Mule SDK. Uses existing Mule components. Built using Maven archetype and deployed to exchange.
    - Types of connectors
        - Community - MuleSoft or members of MuleSoft. No license
        - MuleSoft certified - Developed by partners of MuleSoft and developer community. Contact the partner for support.
        - Select - MuleSoft maintains. Used by everyone but support is only included with an Anypoint platform subscription.
        - Premium - Maintains premium connectors. Active CloudHub premium plan or an Enterprise subscription with an entitlement for the specific connector you wish to use.
    - Scheduler - Event source. Fixed frequency and Cron expression. Some connector event sources can handle watermarks and include a scheduling strategy to trigger a flow. Database: On Table Row. File, FTP, SFTP, FTPS: On New or Updated File.
    - Scheduler behavior vs runtime deployment
        - Customer-hosted or Anypoint runtime fabric deployment: Apps deployed to a cluster run only on the primary node. Standalone apps run on all Mule runtimes.
        - CloudHub deployment: Apps deployed to multiple workers guarantee the scheduler execution on a single worker, subsequent triggers might execute on a different worker. Cron schedules use the UTC time zone, regardless of the geographic region or time zone parameter. Minimum recommended scheduler frequency is 10 seconds.
    - Error generation: Error might originate from Java code (or a called Java library) in the event processor or from a DataWeave expression for the inputs. If not handled, the error message logged and the flow processing stops. If the flow has an event source, a response error message is usually returned.
    - Mapping error types in Mule components: Allows mapping errors to a new type. The new type is a custom namespace and error type. Allows the error to abstract and apply context to underlying failures.
    - Raising errors: Raise error can throw a standard or custom error type. The error type must be a core mule runtime error e.g. MULE:CONNECTIVITY or a custom error type e.g. ORDER:INVALID_DATA. The description is the message in the thrown error.
    - Error handler: An error handler can only be added to a global error handler (outside of any flows), a flow, a try scope and not to sub flows. A global error handler for the entire Mule application.
    - Default error handler: If there is no error handler defined for a flow or try scope, a Mule default error handler is used. Implicitly and globally handles all messaging errors thrown in mule application. Stops execution of the flow and logs information about the error. Automatically rethrows the error. Cannot be configured
    - Error types:
        - On error propagate: Rest of the flow not executed. Error rethrown up to the next level. Return error (5xx) response. The current open transaction is rolled back.
        - On error continue: Rest of the flow not executed. The result of the error handler scope is passed up to the next level. It returns success (2xx) response. The current open transaction is committed.
    - System error handler: When an error does not involve a Mule event, the system error handler is invoked. Examples - The Mule runtime has errors while starting up, like running out of memory. The connection for a database connector goes offline or the network disconnects. The system error handler logs the error, executes the connector’s reconnection strategy if the error was caused by a connection failure. These system errors are not caught by any flow or try scope’s error scopes, nor by any configured global error handlers.
    - Router: A router is a type of scope that uses particular logic to send Mule events to one or more sequences of event processors (also called routes).
        - Choice - Choice router is a scope that performs top-down sequence of conditional tests. Only the first “true” route in the top-down sequence is executed. If no previous conditions are true, the final default condition will execute. Functions like if/else or case statements in other languages.
        - First successful - Iterates through a list of child routers until the first successful execution. If a route fails, the error is logged and then ignored, and then the next route is called. If no routes succeed, the flow stops and the last error is rethrown up the call stack. Useful for failing over to other options if error occurs. After one route succeeds, all other routes are ignored even if they throw errors
        - Round robin - The scope routes the incoming Mule event to only one of its routes. A different route is selected each time in a looping round-robin manner. Each invocation of the round robin router is synchronous. Error in chosen route will stop the flow and the error is rethrown up the call stack.
        - Scatter-gather - This route copies (scatters) a Mule event to two or more parallel routes. Each route uses a separate thread, unless in a transaction. The scatter-gather waits for every route to complete or to time out. The timeout value can be set in the scope. If any route times out, a MULE:TIMEOUT error is generated. At the end, results are combined (gathered) - Even if some routes returned an error. If every route succeeds. Every route’s Mule message is gathered into a single payload. Each route’s index is the key. The gathered Mule event payload contains each route’s result. Access each route’s result payload from the array #[payload..payload]. Variables of all routes are combined into vars. Overlapping variables become arrays. If any route throws an error. An error of type MULE:COMPOSITE_ERROR is thrown. Error contains the result (Mule event or error) of every route, organized as successes or failures, and also includes the error from any routes that timed out. Event processing stops. Instead, the flow’s error handler process the error as they would any other error type. To recover from an individual route error, add error handlers in a try scope or call a separate flow with its own error handler.
    - Walkthrough 3-3: Design an integration application that consumes and combines two external APIs
    - Summary: Event processer, Mule event, payload, variables, connectors, transform message, scopes, flow control, async processing, batch processing.
- **Module 7: Choosing and developing a deployment strategy**
    - Distinguish between various Anypoint platform service models: Control plane - Anypoint exchange, Anypoint design center, and Anypoint management center and runtime plane - Runtime engine and services.
    - Control plane deployment options: MuleSoft hosted - Anypoint platform, AWS regions (Default: U.S. East (N Virginia), EU (Frankfurt)), Government cloud (U.S. Only). Customer hosted - Anypoint platform private cloud edition.
    - Runtime plane deployment options:
        - MuleSoft hosted: Cloud based infrastructure (iPaaS). Provisioned and managed by MuleSoft. CloudHub
        - Customer-hosted: Provisioned and managed by customer. In non-MuleSoft-hosted cloud environments like AWS, Azure, GCP. On-premises: On virtual machines, bare-metal servers, or containers like docker. MuleSoft runtime fabric.
        - In each service mode, the same Mule runtime binary is used in a particular runtime plane.
    - CloudHub 1.0 vs CloudHub 2.0
    
    | CloudHub 1.0 | CloudHub 2.0 |
    | --- | --- |
    | VMs are automatically provisioned with a Mule runtime. This is called a CloudHub worker. One application per worker | Replicas containing a Mule runtime are created and deployed to CloudHub cloud of VMs. Uses Runtime Fabric services. One application per replica |
    | Horizontal: Multiple CloudHub workers.
    Vertical: Resize vCore size used by CloudHub workers | Horizontal: Multiple replicas. Vertical: Resize vCore size used by replicas |
    - Other components of MuleSoft-hosted runtime plane. Load balancing service. Distributes inbound HTTP requests. Automatic redirection after resize or restart. Zero downtime. CloudHub 1.0 shared VPC restricts access to workers to specific ports. 80 maps to 8081. 443 maps to 8082. CloudHub 2.0 shared space restricts access to replicase to a specific port. 443 maps to 8081. Distributed object store and persistent queues service. Data survives restarting/redeploying the Mule application. Both available in CloudHub 1.0. Only persistent object stores are supported in CloudHub 2.0. Persistent queueing is available via Anypoint MQ service.
    - Customer hosted runtime planes. Manually provisioned. Bare-metal servers or in VMs. Allow deployment of multiple mule applications and domains to the same Mule runtime. Host multiple Mule runtimes. Other cloud-based infrastructure can also be locked down. No multiple Mule applications deployment. No Mule domains. No hosting of multiple Mule runtimes on the same virtual machine.
    - Customer responsibilities: Responsible for provisioning and managing all. Hardware, virtual machines, cloud environments, and operating systems. Networks, proxies, load balancing, and high availability services. Java versions and security enhancements.
        
        
        | MuleSoft-Hosted | Customer-Hosted |
        | --- | --- |
        | Mule runtime automatically provisioned in separate CloudHub replica. Host one Mule application per replica | Mule runtimes deployed to on-premises or in the cloud. Run multiple Mule application in one Mule runtime. MuleSoft runtime fabric uses replicas creating single app, single runtime isolation |
        | No contention for host resources | Can have contention for host resources |
        | Automatic updates and patches | Customer must schedule and install updates |
        | Globally available | Customer must provision across regions and multiple premises |
        | MuleSoft-provided security and SLAs | Customer defines and controls security and SLAs |
        | Managed by the MuleSoft-hosted Anypoint platform control plane | Managed by the MuleSoft-hosted or customer-hosted Anypoint platform control plane |
    - Deploying to CloudHub: Only deployment to CloudHub 1.0 are supported from Anypoint studio. CloudHub 1.0 - Scale and CloudHub 2.0 - replicas. Clustering of replicas can also be configured.
    - Walkthrough 7-1: Deploy a Mule application to CloudHub.
    - Deploying to customer-hosted runtime planes: Mule runtime ships with a Runtime manager agent plugin. Securely connects the Mule runtime with Runtime manager on the control plane, to remotely manager and monitor the Mule runtime and its Mule applications. Can expose local REST API.
    - Clustered fault-tolerant deployment: Customer-hosted runtime planes and CloudHub 2.0. Cluster - set of Mule runtimes. Hazelcast-based distributed shared memory grid. For customer-hosted runtime planes, one node will be primary node to run schedulers & event sources configured as primary node only. CloudHub 2.0, runs scheduled jobs on all replicas by default but connectors can be configured to run on primary node: primaryNodeOnly=”true”. All worker nodes work in an active-active model. If one node fails, outstanding tasks transfer automatically to surviving nodes. VM queue message and the primary node is reassigned if needed. Nodes can be added to and subtracted from a cluster to adjust load capacity.
    - Walkthrough 7-2: Deploy a Mule application to a customer-hosted runtime plane
    - Walkthrough 7-3: Deploy a Mule domain and Mule applications to a single Mule runtime
    - Anypoint runtime fabric: Additional software to scale customer-hosted Mule runtimes. Clustered container service that automates and orchestrates the deployment of Mule applications to private cloud infrastructure and on-premises data centers. Mule applications deploy to an isolated Mule runtime in a docker container. Runs on customer-hosted infrastructure. AWS, Azure, Virtual machines (VMs) or bare-metal servers. Requires the use of the control plane hosted by MuleSoft. Two deployment options: On VMs/Bare Metal (also known as the appliance model). Self managed Kubernetes (AKS/EKS/GKE).
    - Runtime fabric on virtual machines / bare metal: Infrastructure provided by customer. Includes Kubernetes (K8s) and docker as MuleSoft-managed software appliances. Support for bare metals or VMs hosted on AWS, Azure, GCP, or physical data centers. Lower need for Kubernetes expertise.
    - Runtime fabric on self-managed Kubernetes: Install runtime fabric services in managed Kubernetes solutions (EKS, AKS, and GKE). Provide and manage your own Kubernetes cluster. Set up your own Ingress controller. More flexibility, cheaper, and less overhead. Kubernetes expertise is required
    - Runtime fabric on OpenShift: OpenShift managed Kubernetes clusters. Provisions a cluster on cloud of your choices (AWS, Azure, Google cloud or bare metal). Autoscaling, load balancing, monitoring cluster health, and alerting are configured
    - Which runtime fabric operating model to use
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%203.png)
        
    - Deploying to Anypoint Runtime Fabric: Runtime manager or Runtime manager API. Deployment target. No support for non-mule applications.
    - Distinguish between various Anypoint Platform deployment models
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%204.png)
        
    - Comparing Anypoint Platform control plane hosting options
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%205.png)
        
    - Comparing Anypoint platform runtime plane hosting options
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%206.png)
        
    - Comparing access to other Anypoint platform runtime services based on the runtime plane type
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%207.png)
        
    - Exercise 7-4: Compare Mule application deployment options for various deployment targets
    - Deciding on deployment options for various scenarios: Regulatory requirements of on-premises processing. Including metadata about API invocations and messages, Time-to-market. IT operations effort. Accessing on-premises data sources. Flexibility of deployment across cloud providers. Isolation between Mule apps. Control over Mule runtime tuning. Scalability of runtime plane. Horizontal and vertical; static and dynamic. Rollout of new releases. Redeployment with zero downtime. High availability. Automated failover. Out-of-the-box features required - object store, shared resource support, persistent queues, scheduling, logging, dashboard, insights, alerts, autoscaling. Anypoint security. Tokenization.
    - Factors for choosing the best runtime plane to use based on organizational business goals
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%208.png)
        
    - Choosing the best runtime plane based on performance and reliability goals
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%209.png)
        
    - Choosing the best runtime plane based on deployment flexibility goals
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%2010.png)
        
    - Choosing the best runtime plane based on reusability and isolation goals
        
        ![Untitled](Initiating%20integration%20solutions%20on%20Anypoint%20Platf%20f2ed69ad05054654b068e79023d16c71/Untitled%2011.png)
