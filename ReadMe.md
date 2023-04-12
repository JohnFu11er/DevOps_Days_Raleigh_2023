# DevOps Days Raleigh 2023 Notexs
<img src="./pictures/devops_days_logo.jpg" width="200">

### Resources
- [OpenTelemetry](https://opentelemetry.io/)
- [Theory of control systems](https://en.wikipedia.org/wiki/Control_theory)
- [Example of microservices (humor)](https://www.youtube.com/watch?v=y8OnoxKotPQ)
- [KubeEdge](https://kubeedge.io/en/)
- [EdgeMesh](https://edgemesh.com/)
- [Container Networking Interface (CNI)](https://github.com/containernetworking/cni)
- [Service Mesh](https://konghq.com/learning-center/service-mesh/what-is-a-service-mesh)
- [Ambient](https://www.solo.io/products/ambient-mesh/)
- [HTTP-Based Overlay Network (HBONE)](https://istio.io/latest/blog/2022/introducing-ambient-mesh/)
- [GLOO platform](https://www.solo.io/products/gloo-platform/)
- [Edge Computing Systes Kubernetes technologies](https://www.amazon.com/Edge-Computing-Systems-Kubernetes-technologies/dp/1800568592)
- [Itsio Ambient Explained](https://www.oreilly.com/library/view/istio-ambient-explained/9781098142698/)
- [Cypress](https://www.cypress.io/)
- [Testing Fundamentals](https://automationpanda.com/2020/07/07/arrange-act-assert-a-pattern-for-writing-good-tests/)
- [Feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
- [AzureAD](https://azure.microsoft.com/en-us/products/active-directory/)
- [Okta](https://www.okta.com/)
- [Ping](https://www.pingidentity.com/en/platform/capabilities/single-sign-on.html)


### Sections
- [Observability vs performance monitoring](#observability-vs-performance-monitoring)
- [Edge Compute Ops](#edge-compute-ops)
- [Testing in Prod as Part of the Pyramid](#testing-in-prod-as-part-of-the-pyramid)
- [Zero Trust Security for K8's apps](#zero-trust-security-for-k8s-apps)

### Observability vs performance monitoring
- [Sarah Morgan](https://www.linkedin.com/in/sarahgmorgan/)
- Works at [Telemetry Hub](https://telemetryhub.com/)
- Distributed systems are harder to monitor
- How do we monitor ephemeral resources?
- How do we determine metastable states? (it looks like everything is good, but it's not)
- Get to the point of understanding the state of the internal system by observing the output
- Observability is the ability to tell what is going on
- Monitoring is keeping track of what is going on in your system
- Observability is a scale, not on or off
- Comes from the [theory of control systems](https://en.wikipedia.org/wiki/Control_theory) from 1960
- Goal is to answer the unknowns
  - What is the error rate on a specific endpoint?
  - If a customer is having a bad experience, it doesn't matter if all of the monitoring metrics are green
- Monitoring metrics should be as available as possible to all members of your development and operations teams
- Atempt to determine correlation between different monitoring outputs
- [Example of microservices](https://www.youtube.com/watch?v=y8OnoxKotPQ)
- When considering effecitness of a monitoring system, can you answer:
  - WHo is impacted?
  - What do I have to do to resolve it?
  - Where is the problem?
  - When did the issue start?
  - Why did we end up in this state?
- Pillars of observability:
  - `Metrics`
    - Best for statistical information in aggregate
  - `Distributed Traces`
    - Trace a request from start to finish
    - Requires trce and span ids to be propagated so that all of the players can account for all services in the chain of product resources
  - `Logs`
- [OpenTelemetry](https://opentelemetry.io/)
  - Open source monitoring solution
  - Has SDK for development in several languages
  - OTel collector:
    - Receive data
    - Process data
    - Export data
  - No storage or visualization solutions in OpenTelemetry

### Edge Compute Ops
- [Marino Wijay](https://www.linkedin.com/in/mwijay/)
- How do I view what is happening on my edge application deployment
- Tools:
  - Graphana
  - Promethesius
- [KubeEdge](https://kubeedge.io/en/)
- [EdgeMesh](https://edgemesh.com/)
- K3
- [Container Networking Interface (CNI)](https://github.com/containernetworking/cni)
- [Service Mesh](https://konghq.com/learning-center/service-mesh/what-is-a-service-mesh)
  - Sidecar vs. applicaion
  - [ambient](https://www.solo.io/products/ambient-mesh/)
- Networking problems:
  - VPN
  - Tunnelling
- [HTTP-Based Overlay Network (HBONE)](https://istio.io/latest/blog/2022/introducing-ambient-mesh/)
  - Just a fancy Istio "protocol" for using HTTP Connect to tunnel encrypted data
- [GLOO platform](https://www.solo.io/products/gloo-platform/)
  - Can help solve some of these challenges:
    - Zero trust security architecture for APIs and microservices
    - Combine north-south and east-west traffic management (API gateway + service mesh)
    - Unified failover and security policy across gateway and mesh 
    - Aligning with the leading approaches to software development
    - Scale across multiple dimensions (multi-cluster, multi-tenant, multi-cloud)
- Books for follow up:
  - [Edge Computing Systes Kubernetes technologies](https://www.amazon.com/Edge-Computing-Systems-Kubernetes-technologies/dp/1800568592)
  - [Itsio Ambient Explained](https://www.oreilly.com/library/view/istio-ambient-explained/9781098142698/)

### Testing in Prod as Part of the Pyramid
- [Cecilia Martinez](https://github.com/ceceliacreates)
- Testing tools
  - [Cypress](https://www.cypress.io/)
- Testing methodologies
  - The testing crab
  - Unit testing pyramid
- Testing development should consider:
  - Types of testing
  - Coverage goals
    - How much of the code-base to cover
    - How many of the features
    - Be intentional with your testing
  - Test maintenance
  - Ask:
    - "How can I test before production and in production?"
    - "How can I take test results from production back into pre-production development?
- Tesing in Prod: definitions
  - New code changes are tested on live user traffic
- Pogressive delivery:
  - Ship features, not releases
  - Greater shift to testing in prod
- Benefits:
  - Greater environmental accuracy
  - Improves deployment agility
  - More nuanced testing results
- [Testing Fundamentals](https://automationpanda.com/2020/07/07/arrange-act-assert-a-pattern-for-writing-good-tests/)
  - Arrange
  - Act
  - Assert
- Limits
  - Requires modern deployments
  - Data and security management strategy needed
  - Potential for outages or bugs related to implementation
- Testing types:
  - Quality
  - Performance
  - Security
  - Stress
  - Recovery
- [Feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
  - Toggle functionality without deploying new code
  - Used for graduated rollouts or split testing
  - Rollback features easily
- Observe and monitor:
  - Monitoring: gathering pre-defined metrics
  - observability: finding things that we don't know
- Other tools can capture:
  - Product usage analytics
  - Session replay
  - Qualitative data collection
    - User feedback
- Testing in Prod: strategy
  - It's still testing
  - Feature experimentation
    - Split testing with [feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
    - Investment in product usage analytics
    - Strict definitions of success and test conclusion criteria
  - Production uncertainty
    - Prod env difficult to reproduce for testing
    - Rollouts with [feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
    - Investment in monitoring with defined events
    - Recovery plan strategy
  - Usabiliity
    - Product and UX validation
    - Split testing with [feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
    - Investmnt in session replay and qualitative data collection
  - Experimental
    - Identifying unknowns
    - Not confident all test cases discovered
    - Rollouts with [feature flags](https://www.atlassian.com/continuous-delivery/principles/feature-flags)
    - Investment in observability
- Other things of interest:
  - [Monte Carlo Simulation](https://www.investopedia.com/terms/m/montecarlosimulation.asp)

### Zero Trust Security for K8's apps
- Identity based security
  - [AzureAD](https://azure.microsoft.com/en-us/products/active-directory/)
  - [Okta](https://www.okta.com/)
  - [Ping](https://www.pingidentity.com/en/platform/capabilities/single-sign-on.html)
- Ingress controllers
  - Policy Decision Point (PDP)
  - Policy Enforcement Point (PEP)
- Features and capabilities
  - Authentication and Authorization
  - Data encryption and integrity
  - Access control and access
  - Monitoring and observability
  - WAF and DoS protection
- Best practices:
  - avoid complexity and overhead
  - enforce zero trust for comms to/from and within the k8s cluster
  - secure n=s comms with an ingress controller and e-w comms with a service mesh
  - integrate the ingerss controller with the service mesy
  - Automate certificate management
- Benefits
  - Protext apps from edge to cloud
  - Prevent unauthorized activity
  - Minimize atack surface
  - Ensure holistic app security
  - Gain better visibility and insight
  - Reduce complexity and sprawl
- - Additional documentation
  - [Zero Trust Architecture in Kubernetes](https://www.nginx.com/resources/library/zero-trust-architecture-in-kubernetes/)