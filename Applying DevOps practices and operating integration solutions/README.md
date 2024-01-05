# Applying DevOps practices and operating integration solutions

- **Topics**
    - Create high-level designs of CI/CD pipelines for Mule applications using MuleSoft-provided maven plugins
    - Identity the features and characteristics for automating interactions with Anypoint platform
    - Design the logging configurations and options of Mule applications in all deployment options
    - Identify the features and characteristics of Anypoint monitoring in all deployment option
- **Modules**
    
    Module 9 and  Module 10
    
- **Module 9: Designing effective logging and monitoring**
    
    Logging related: Auditing and logging options, logging strategies, logging policies, third-party log management system.
    
    - Audit: Audit logs for Anypoint platform interactions. Control plane alone. Organization owner. Audit Log Viewer permission. Trace access violations. **Audit log is queryable. Retained for six years.** View and download from Anypoint platform Access Management UI and use the **Audit Logging Query API**.
    - Logging options: Standard slf4j and log4j2 logging. Log levels - DEBUG, TRACE, INFO (default log level), WARN, and ERROR. Appenders - system console, a file, a database, the CloudHub logging service, or another server or service.
    - **CloudHub - Up to 100 MB per Mule application and per worker. At most 30 days.**
    - System log and application logs in CloudHub and customer-hosted runtime planes. System.out messages are in system logs for customer-hosted runtime plane and in application logs for CloudHub
    - Synchronous and asynchronous logging.
        - Synchronous: Message interrupted, waits, degrades performance, useful for audit trail or ERROR/CRITICAL messages, not **supported in CloudHub**
        - Asynchronous: Separate thread, substantial improvement in throughput and latency, **log lost in case of system crash**
    - CloudHub log settings: Asynchronous and log level greater then INFO. By default DEBUG and TRACE level messages are ignored. **Runtime manager override log level without redeployment.**
    - **Mapped diagnostic context (MDC):** Provides more context or information, Mule tracing module, changing pattern in the log4j2.xml.
    - Correlation ID: To trace log messages. **Header : X-Correlation-ID.** Modified with custom generator expression. Tracing module with-correlation-id scope
    - **CloudHub provided log4j2.xml file replaces the Mule application’s log4j2.xml file.**
    - External systems: **Disable the CloudHub logs and use the Mule application’s log4j2.xml file.** Support portal request for CloudHub 1.0 and default for CloudHub 2.0. **System log can’t be exported.** CloudHub log4j2 appender.
    - Fetch logs using **CloudHub APIs** and send to an external system. Not recommended.
    - Customer-hosted runtime planes:  **Splunk or ELK runtime manager agent plugins**. Configured through **Runtime Manager web UI**. Plugins can be developed. Fetch or scrape logs from Mule Runtime. Add log4j-specific system appenders to the Mule runtime.
    
    Monitoring related: Anypoint platform monitoring, alerting, notification, visualization, and reporting options for APIs and integration solutions
    
    - Anypoint monitoring and API functional monitoring.
    - Platinum subscription - Application performance monitoring and custom metrics & events.
    - Titanium subscription - All including log management
    - How to enable
        - CloudHub - Enable/disable monitoring of individual applications vis UI in the setting menu of Anypoint monitoring. Also from runtime manager application setting for each application. **By default all CloudHub 2.o applications are enabled for Anypoint monitoring.**
        - On-prem - **Download and install the Anypoint monitoring agent. It sends data to the Anypoint monitoring.** Mule runtime versions: 3.8.7, 3.9.x, and 4.x.x are supported
        - Runtime fabric - **By default all applications are enabled for Anypoint monitoring**
    - Dashboards
        - **Needs special permissions to view the dashboards**
        - Built-in dashboard - Metrics like inbound & outbound events, performance, infrastructure, JVM, failures. **Visualized graphically in the Application network or via Anypoint Visualizer**
        - Custom dashboard
    - Alerts
        - Basic alerts and advanced alerts - **Mule applications and servers**. Different set of alerts for each.
        - These alerts are distinct from API manager alerts and runtime manager alerts.
        - **CloudHub - Message count, message error count, message response time, CPU utilization, memory utilization, thread count**
        - **On-prem - Message count, message error count, message response time**
        - **Server - CPU utilization, memory utilization, thread count**
    - Log management - **Log points - codeless logging**, extensive logging may degrade performance.
    - **Custom metric connector** - Titanium features, for custom dashboard. Alternative to using logger component to visualize certain business metrics.
    - **Insights or business events** - Degrades application performance at volume. KPI data
    - **Health check endpoints**
    - Mule runtime agent - Third party integrations. Download mule agent → register agent to ARM → Send mule event or API analytics→ To Splunk or ELK
    
    Anypoint Functional Monitoring
    
    - Functional monitors - Invoking APIs, external APIs as well. Create directly or upload. BDD (Behavior Driven Development). Supports multiple endpoints and assertions in a monitor. Receive failure reports through the third party integrations - NewRelic, PagerDuty, Slack, SumoLogic, Email
        - Public locations - Public APIs, maximum of 5 monitors and shortest execution interval 15 minutes (non-titanium) cron (titanium)
        - Private locations - Private APIs CloudHub VPC or private space. Requires 0.2 vCores. Shortest execution interval 5 minutes (non-titanium) cron (titanium)
    - Testing - Write tests manually and schedule them with the black box automated testing (BAT) CLI. DataWeave expressions. BAT CLI for CI/CD pipeline.
    
    Anypoint Analytics Dashboard
    
    - Charts - Requests by date, requests by location, requests by application, and requests by platform
    - API reporting - CSV or JSON
    
    Visualization options
    
    - Nodes: application components - system, process, and experience
    - Edge: request-response interactions
    - Data collection through Mule runtime and connectors
    
    Runtime Manager
    
    - Alerts - **No support for RTF deployed applications. RTF has built-in alerting capabilities. Based on Kapacitor**
    - **Alert conditions**
        
        ![Untitled](Applying%20DevOps%20practices%20and%20operating%20integratio%20a71c8ff4c3a24ae8bbcdc4b8fe21103a/Untitled.png)
        
        ![Untitled](Applying%20DevOps%20practices%20and%20operating%20integratio%20a71c8ff4c3a24ae8bbcdc4b8fe21103a/Untitled%201.png)
        
- **Module 10: Designing an efficient and automated software development lifecycle**
    
    Manage properties files, manage Anypoint Platform environments, implement CI/CD, automated deployment and management with Anypoint Platform
    
    Properties
    
    - Mule application-level properties and system-level properties
    - **Externalize Mule application properties files outside the Mule runtime for customer-hosted Mule runtime.**
    - Environments: Production, sandbox, design (flow designer)
    
    CI/CD
    
    - Mule Maven Plugin - Automate building, packaging, and deployment of Mule applications from source projects
    - MUnit Maven Plugin - Automate test execution, and it ties in with the Mule Maven Pugin
    - **Exchange Mule Maven Plugin** - Used internally by the Mule Maven Plugin for deployment to exchange. Custom artifacts like poms and external jars. **Requires pre-deploy goal to validate the asset.**
    - **Mule Extension Maven Plugin** - To create mule-plugin artifact.
    - Anypoint Exchange - Central repository. RAML fragments, custom connectors, and project templates & examples. Maven-compatible artifact repository - **is not intended as a replacement for a full version control system**
    - Maven lifecycles - compile > test > package > install > deploy
    
    Deployments
    
    - **CloudHub 2,0**
    - **CloudHub 1.0**
    - **Anypoint Runtime Manager**
    - **Standalone runtimes**
    - **Mule agents**
    
    ![Untitled](Applying%20DevOps%20practices%20and%20operating%20integratio%20a71c8ff4c3a24ae8bbcdc4b8fe21103a/Untitled%202.png)
    
    Automation on Anypoint Platform
    
    - For administrative activities
        - **Anypoint CLI** - Combines REST API steps into easier-to-use commands. Node.js based. Authentication using username and password
        - **Anypoint platform APIs** - Generate access token or use OAuth 2.0. Use the access token in other REST calls. Set the environment ID or organization ID as needed.
        
    
- **Questions**