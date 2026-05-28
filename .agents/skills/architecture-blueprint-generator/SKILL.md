---
name: architecture-blueprint-generator
description: "Focused architecture blueprint generator that produces detailed documentation across seven key dimensions: application architecture diagrams, dataflows and schemas, external dependencies, technology stack, platform/deployment architecture, non-functional requirements, and QA test coverage. Automatically detects and visualizes these dimensions while explicitly noting gaps."
---

# Architecture Blueprint Generator — 8 Key Dimensions

## Configuration Variables

${PROJECT_TYPE="Auto-detect"} <!-- Primary technology stack -->
${ANALYSIS_DEPTH="Comprehensive"} <!-- Analysis scope: Quick, Standard, Comprehensive -->
${INCLUDE_DIAGRAMS=false} <!-- Generate visual diagrams -->
${REFERENCE_CODEBASE_DOCS=true} <!-- Reference docs/codebase/ documents if available -->
${REPORT_GAPS=true} <!-- Explicitly note items not evident in codebase -->
${GENERATION_TIMESTAMP="YYYY-MM-DD_HHMMSS"} <!-- Timestamp for filename audit trail -->

## Table of Contents

1. [Application Architecture Diagram](#1-application-architecture-diagram)
2. [Dataflows and Schema Diagrams](#2-dataflows-and-schema-diagrams)
3. [External Dependencies](#3-external-dependencies)
4. [Technology Stack](#4-technology-stack---application-and-engineering)
5. [Platform/Deployment Diagram](#5-platformdeployment-diagram)
6. [Non-Functional Requirements (NFR)](#6-non-functional-requirements-nfr)
7. [QA Test Types and Coverage](#7-qa-test-types-and-coverage)
8. [Techical Debt/Compliance with NHSE Principles](#8-technical-debtcompliance-with-nhse-principles)

## Generated Prompt

"Create a focused 'docs/Project*Architecture_Blueprint*${GENERATION_TIMESTAMP}.md' document that comprehensively documents the codebase architecture across seven key dimensions. For any dimension not evident in the codebase, explicitly state 'Not evident in the codebase' rather than leaving it blank. Reference `docs/codebase/` documents if available in the repository. Use the following approach:

### 1. Application Architecture Diagram

${INCLUDE_DIAGRAMS ? `Create a clear visual diagram (C4 Model or architecture diagram) showing:

**High-level Components:**

- Major system components and subsystems
- Component responsibilities and boundaries
- Primary communication paths between components
- Organizational patterns (layered, microservices, monolithic, etc.)

**Interactions:**

- Synchronous vs. asynchronous communication patterns
- External system integrations (if any)
- Data flow between components
- API/service boundaries

**Output:**

- Provide both a visual diagram and a textual description
- Ensure the diagram reflects the actual implementation in the codebase` : ""}

**Not Found:**
${REPORT_GAPS ? "If application architecture is not evident in the codebase (e.g., early-stage projects, template/example repositories), explicitly state: **'Not evident in the codebase: Application architecture diagram could not be determined from available code structure.'**" : ""}

### 2. Dataflows and Schema Diagrams

**Data Movement:**

- Document how data flows through the system
- Identify data sources (databases, APIs, files, streams, etc.)
- Map data transformations and processing pipelines
- Note batching, streaming, or real-time processing approaches

**Schema Documentation:**

- Document database schema (tables, relationships, constraints)
- Document API request/response schemas
- Identify data validation rules
- Note any data caching or persistence layers
- Document message formats (if event-driven or async messaging)

**Data Lineage:**

- Track data from source → transformation → storage → consumption
- Identify critical data paths and dependencies
- Document data lifecycle (creation, modification, deletion)

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/ARCHITECTURE.md' (if available) for documented data architecture patterns.` : ""}

**Not Found:**
${REPORT_GAPS ? "If dataflows and schemas are not evident, explicitly state: **'Not evident in the codebase: Data flows and schema information could not be determined.'**" : ""}

### 3. External Dependencies

**Third-Party Integrations:**

- Document all external APIs, services, and systems the application depends on
- For each dependency:
  - **Service Name & Purpose**: What it provides
  - **Integration Method**: REST API, gRPC, webhook, SDK, plugin, MCP, etc.
  - **Authentication/Credentials**: How authentication is handled
  - **Data Format**: JSON, XML, Protocol Buffers, etc.
  - **Resilience**: Timeout, retry, fallback strategies
  - **Cost/Licensing**: If applicable

**Infrastructure Dependencies:**

- Cloud providers (AWS, Azure, GCP, etc.)
- Databases and storage systems
- Message brokers and queues
- Monitoring and logging platforms
- Build and deployment systems

**Library and Framework Dependencies:**

- Major language frameworks and runtime
- Critical third-party libraries (version constraints)
- Development tools and plugins

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/INTEGRATIONS.md' and 'docs/codebase/STACK.md' (if available) for comprehensive dependency lists.` : ""}

**Not Found:**
${REPORT_GAPS ? "If external dependencies are not evident, explicitly state: **'Not evident in the codebase: External dependencies and integrations could not be identified.'**" : ""}

### 4. Technology Stack — Application and Engineering

**Application Stack:**

- **Languages**: Primary and secondary languages used
- **Frameworks & Runtimes**: Web frameworks, application servers, runtime environments
- **Databases**: Type (SQL, NoSQL, document store, etc.) and specific systems
- **Libraries**: Key libraries and their purposes
- **APIs**: RESTful, GraphQL, SOAP, gRPC, or custom protocols

**Engineering Stack:**

- **Build Tools**: Compilers, transpilers, bundlers, build frameworks
- **Package Management**: npm, pip, Maven, Gradle, NuGet, etc.
- **Version Control**: Git, branching strategy, commit conventions
- **Testing Tools**: Unit test frameworks, integration test tools, load test tools
- **Code Quality**: Linters, formatters, static analysis tools
- **CI/CD**: Build pipelines, deployment automation, testing automation
- **Documentation**: Documentation generation tools, architecture documentation approach
- **Monitoring & Observability**: Logging, metrics, tracing, APM tools

**Architectural Patterns Enabled by Stack:**

- How does the chosen stack support the application architecture?
- Technology constraints or enablers

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/STACK.md' (if available) for a comprehensive technology analysis.` : ""}

**Not Found:**
${REPORT_GAPS ? "If technology stack is not evident, explicitly state: **'Not evident in the codebase: Complete technology stack information could not be determined.'**" : ""}

### 5. Platform/Deployment Diagram

**Deployment Topology:**

- Document how the application is deployed across environments (dev, staging, production)
- Identify nodes, containers, services, and their relationships
- Show load balancing, clustering, redundancy, and failover mechanisms
- Document network topology and security boundaries

**Environment Configuration:**

- **Development**: Local development setup, containerization, required services
- **Testing**: Test environment topology, test data strategies
- **Staging**: Pre-production environment configuration
- **Production**: Production deployment architecture, scaling strategy, disaster recovery

**Containerization & Orchestration:**

- Docker images, container registries
- Kubernetes manifests, Helm charts (if applicable)
- Container orchestration strategy
- Service mesh or networking approach

**Infrastructure as Code:**

- Terraform, CloudFormation, ARM templates, or other IaC tools
- Infrastructure configuration and provisioning approach
- Environment variable and secret management

**Deployment Process:**

- CI/CD pipeline steps
- Automated deployment vs. manual steps
- Rollback and rollforward strategies
- Release management process

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/ARCHITECTURE.md' (if available) for deployment layer documentation.` : ""}

**Not Found:**
${REPORT_GAPS ? "If platform/deployment architecture is not evident, explicitly state: **'Not evident in the codebase: Deployment topology and platform architecture could not be determined.'**" : ""}

### 6. Non-Functional Requirements (NFR)

**Scalability:**

- Horizontal scaling approach (stateless design, load balancing, distributed caching)
- Vertical scaling considerations
- Database scaling strategy (sharding, replication, read replicas)
- Identified performance bottlenecks and mitigation strategies
- Peak load capacity and scaling triggers

**Security:**

- Authentication mechanisms (OAuth, JWT, API keys, mTLS, etc.)
- Authorization model (RBAC, ABAC, custom policies)
- Data encryption (at rest and in transit)
- Input validation and sanitization
- Security boundary enforcement
- Compliance requirements (GDPR, HIPAA, PCI-DSS, etc.)
- Vulnerability scanning and patching strategy

**Reliability & Availability:**

- Target uptime/SLA (e.g., 99.9%, 99.99%)
- Failure modes and recovery strategies
- Health checks and liveness probes
- Circuit breakers and bulkheads
- Graceful degradation and fallback mechanisms
- Disaster recovery and business continuity planning

**Performance:**

- Response time targets (p50, p95, p99 latencies)
- Throughput targets (requests/second, messages/second)
- Memory and CPU constraints
- Caching strategies (application, database, CDN, HTTP)
- Query optimization and indexing strategies

**Maintainability:**

- Code organization and modularity
- Documentation standards
- Logging and debugging capabilities
- Configuration externalization
- Feature flags and safe rollout mechanisms

**Monitoring & Observability:**

- Metrics collected and their targets
- Logging strategy (structured logs, log aggregation)
- Distributed tracing (if applicable)
- Alert thresholds and on-call procedures
- Dashboards and visualization tools

**References:**
${REFERENCE_CODEBASE_DOCS ? `Review 'docs/codebase/ARCHITECTURE.md' for documented reliability and performance patterns.` : ""}

**Not Found:**
${REPORT_GAPS ? "If non-functional requirements are not evident, explicitly state: **'Not evident in the codebase: Non-functional requirements documentation is not available in the current codebase.'**" : ""}

### 7. QA Test Types and Coverage

**Test Framework & Tools:**

- Unit test framework and conventions
- Integration test approach and tools
- End-to-end (E2E) test framework and coverage
- Performance and load testing approach
- Security testing (SAST, DAST, dependency scanning)
- Testing tools used and their configurations

**Test Categories:**

**Unit Tests:**

- Testing strategy for individual components/units
- Mocking and stubbing approach
- Coverage targets
- Location and naming conventions

**Integration Tests:**

- API integration testing (if applicable)
- Database integration testing
- External service mocking strategy
- Contract testing (if microservices)

**End-to-End Tests:**

- User journey testing approach
- Test data management
- Environment setup for E2E tests
- Headless browser or API-level testing

**Performance Tests:**

- Load testing scenarios and tools
- Stress testing approach
- Performance benchmarks and targets
- Profiling and optimization strategy

**Security Tests:**

- Static code analysis (SAST)
- Dynamic application security testing (DAST)
- Dependency vulnerability scanning
- API security testing
- Authentication/authorization testing

**Manual Testing:**

- UAT (User Acceptance Testing) approach
- Exploratory testing strategy
- Regression testing process

**Test Coverage:**

- Code coverage targets (line coverage, branch coverage)
- Critical path coverage focus
- Coverage measurement and reporting
- Coverage trend over time

**Testing Pipeline:**

- Automated test execution (CI/CD integration)
- Test environment requirements
- Parallel vs. sequential test execution
- Test result reporting and failure analysis

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/TESTING.md' (if available) for detailed testing patterns and validation infrastructure.` : ""}

**Not Found:**
${REPORT_GAPS ? "If QA test types and coverage information is not evident, explicitly state: **'Not evident in the codebase: Test framework and coverage information could not be determined. This may indicate a documentation gap or early-stage project.'**" : ""}

### 8. Technical Debt/Compliance with NHSE Principles

**Technical Debt Overview:**

- Known technical debt areas and documented concerns
- Legacy code, outdated patterns, or deprecated dependencies
- Architectural compromises or temporary workarounds
- Areas requiring refactoring or redesign
- Impact of technical debt on maintainability, scalability, security, and delivery
- Prioritisation approach for addressing technical debt

**Approved Technologies and Standards:**

- Use of approved programming languages, frameworks, libraries, and platforms
- Alignment with organisational technology standards
- Evidence of unsupported, deprecated, or non-standard technologies
- Dependency management and version control approach
- Cloud, hosting, and infrastructure technology compliance
- Rationale for technology choices where non-standard tools are used

**Ways of Working:**

- Development workflow and branching strategy
- Code review process and approval requirements
- Definition of Done and quality gates
- Coding standards, linting, formatting, and naming conventions
- Documentation expectations for code, APIs, infrastructure, and decisions
- Approach to onboarding, knowledge sharing, and reducing key-person dependency

**Codebase Maintainability:**

- Code structure, modularity, and separation of concerns
- Readability and consistency of implementation patterns
- Complexity hotspots and duplicated logic
- Error handling, logging, and observability practices
- Configuration management and environment-specific settings
- Testability of the codebase and ease of change

**Architecture and Design Concerns:**

- Alignment with documented architecture or solution design
- Use of architectural decision records or equivalent documentation
- Known design trade-offs, constraints, or limitations
- Coupling between components, services, or systems
- Scalability and resilience considerations
- Data flow, integration, and interface design concerns

**NHS Principles and Compliance:**

- Alignment with NHS service standards, clinical safety, and information governance expectations
- Compliance with NHS Digital, NHS England, or local trust technology principles where applicable
- Accessibility considerations, including WCAG alignment where user interfaces are present
- Data protection, GDPR, and privacy-by-design considerations
- Security-by-design practices and alignment with NHS cyber security expectations
- Auditability, traceability, and accountability of system changes

**Clinical Safety and Risk Management:**

- Evidence of clinical safety assessment where applicable
- Hazard logs, risk assessments, or safety case documentation
- Clear ownership of clinical safety responsibilities
- Impact of technical debt on clinical safety or operational risk
- Escalation process for safety-related defects or risks
- Validation approach for clinically significant workflows or data

**Operational Readiness:**

- Support model and operational ownership
- Monitoring, alerting, and incident response arrangements
- Backup, restore, and disaster recovery considerations
- Deployment and rollback procedures
- Runbooks or operational documentation
- Known operational risks caused by technical debt

**Security, Governance, and Assurance:**

- Evidence of secure development lifecycle practices
- Secrets management and secure configuration handling
- Access control and least-privilege principles
- Audit logging and traceability of user/system actions
- Dependency and vulnerability management
- Assurance activities, approvals, or governance checkpoints

**Remediation and Improvement Plan:**

- Prioritised list of technical debt items
- Severity, impact, and risk rating for each concern
- Short-term mitigations versus long-term fixes
- Ownership and target resolution dates
- Dependencies or blockers to remediation
- Process for tracking and reviewing technical debt over time

**References:**
${REFERENCE_CODEBASE_DOCS ? `Consult 'docs/codebase/CONCERNS.md' (if available) for documented technical debt, architectural concerns, compliance risks, and known deviations from approved standards. Use CONCERNS.md as much as possible.` : ""}

**Not Found:**
${REPORT_GAPS ? "If technical debt, compliance, or NHS principles information is not evident, explicitly state: **'Not evident in the codebase: Technical debt and NHS compliance information could not be determined. This may indicate a documentation gap, missing concerns register, or early-stage project.'**" : ""}

---

## Summary & Context Reference

**Generated Date & Filename:** [Auto-filled with generation timestamp in format YYYY-MM-DD_HHMMSS]

- Output filename: `docs/Project_Architecture_Blueprint_YYYY-MM-DD_HHMMSS.md`
- This timestamp provides an audit trail of when the blueprint was generated

**Codebase Context:**
${REFERENCE_CODEBASE_DOCS ? `This blueprint references docs/codebase/ documentation files when available:

- ARCHITECTURE.md — System design and component architecture
- STACK.md — Technology stack and dependencies
- TESTING.md — Testing patterns and validation framework
- INTEGRATIONS.md — External APIs and integrations
- STRUCTURE.md — Directory layout and organization
- CONVENTIONS.md — Naming conventions and coding standards

These documents (if found) provide additional context for understanding the codebase architecture.` : ""}

**Maintenance Recommendations:**

- Review and update this blueprint quarterly or when major architecture changes occur
- Add or remove gaps as the codebase evolves
- Link to specific code files and examples to keep documentation current
- Track architectural decisions and their rationales in decision records"
