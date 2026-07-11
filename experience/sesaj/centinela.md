# Centinela

## Overview

Centinela is the interoperability monitoring platform developed as part of the SESAJ ecosystem to continuously validate the availability, health, and compliance of government services connected to the National Digital Platform (PDN).

Unlike Bóveda, which is responsible for secure credential management, Centinela focuses on operational monitoring. Its purpose is to execute automated validations against hundreds of external government services, detect failures early, provide operational visibility, and generate evidence that each public entity complies with interoperability requirements.

The platform performs continuous health checks, functional validations, interoperability testing, historical analysis, and operational dashboards, allowing technical teams to supervise the entire interoperability ecosystem from a single application.

Centinela was designed as an independent microservice to isolate monitoring workloads from credential management while allowing future horizontal scaling as the number of connected entities increases.

---

## Business Context

Connecting a public entity to the National Digital Platform is only the first step.

Once an organization becomes interoperable, its services must remain available continuously. Authentication endpoints, API contracts, SSL certificates, response times, and interoperability requirements must all continue working correctly over time.

Without continuous monitoring, service failures could remain undetected until another government institution attempted to consume information, affecting the reliability of the entire interoperability ecosystem.

SESAJ required a platform capable of automatically validating hundreds of external services, collecting operational evidence, and providing technical teams with complete visibility into the health of every connected public entity.

---

## Product Overview

Centinela automates the operational validation of interoperability services exposed by public entities.

The platform provides:

- Continuous health monitoring.
- Functional validation of interoperability services.
- Automated interoperability testing.
- Scheduling of recurring validations.
- Historical execution records.
- Operational dashboards.
- Public entity profiles.
- Availability metrics.
- Validation history.
- Public digital records of interoperability status.

Instead of storing sensitive credentials locally, Centinela securely requests temporary credential resolution from the Institutional API whenever validation is required.

This architecture keeps monitoring isolated while preserving security boundaries established by Bóveda.

---

## Architecture

Centinela was designed as an independent backend service responsible exclusively for monitoring and interoperability validation.

The service communicates with the Institutional API whenever credentials are required but never persists sensitive information locally.

Each interoperability monitor belongs to a specific public entity and contains its own execution schedule, validation configuration, historical executions, and operational metrics.

Validation requests are executed asynchronously using FastAPI BackgroundTasks, preventing long-running interoperability tests from blocking incoming HTTP requests.

A scheduler continuously evaluates monitoring schedules, queues pending executions, and distributes validations without overwhelming external government services.

Results are persisted independently and exposed through operational dashboards used by technical administrators.

---

## My Contributions

I was responsible for the architecture, design, and implementation of Centinela from the ground up.

My contributions included:

- Designing the monitoring platform architecture.
- Defining service boundaries between Bóveda, the Institutional API, and Centinela.
- Designing relational database models.
- Designing REST APIs and service contracts.
- Implementing backend services using FastAPI.
- Developing Angular frontend modules.
- Designing the monitoring scheduler.
- Implementing asynchronous validation workflows.
- Designing interoperability validation profiles.
- Building operational dashboards.
- Developing monitoring timelines and execution history.
- Implementing dependency and organization management.
- Designing the digital interoperability record for each public entity.
- Implementing monitoring activation workflows.
- Developing validation execution pipelines.
- Automating deployments using GitHub Actions.
- Deploying production services on AWS.

---

## Engineering Decisions

### Independent Monitoring Service

Centinela was intentionally separated from Bóveda to isolate monitoring workloads from credential management.

Monitoring external government services generates continuous network traffic and scheduled workloads that should not impact the platform responsible for storing sensitive institutional information.

This separation also allows monitoring services to scale independently as the number of connected public entities increases.

---

### Secrets Never Leave Bóveda

One of the most important architectural decisions was preventing Centinela from storing credentials.

Whenever validation is required, credentials are securely resolved through the Institutional API.

This guarantees that sensitive information always has a single owner while reducing security risks and avoiding data duplication.

---

### Queue-Based Scheduler

Government entities often share similar monitoring schedules.

Executing hundreds of interoperability validations simultaneously could overload both Centinela and external government services.

To avoid this problem, the scheduler evaluates execution times continuously and queues pending validations instead of launching every monitor simultaneously.

This approach distributes system load while maintaining predictable execution behavior.

---

### Asynchronous Validation

Interoperability validations may involve multiple HTTP requests to external services.

Executing those validations synchronously would block API workers and reduce platform responsiveness.

BackgroundTasks were used to execute validations asynchronously, allowing API requests to return immediately while monitoring continues independently.

---

### Validation Profiles

Different operational scenarios require different levels of validation.

Instead of executing every interoperability check every time, the platform supports multiple validation profiles.

Health Profile

- Basic connectivity verification.
- Authentication endpoint validation.

Simple Profile

- Connectivity.
- Authentication.
- Initial interoperability validation.

Full Profile

- Complete interoperability validation.
- API contract verification.
- SSL validation.
- Response analysis.
- Pagination checks.
- Performance verification.
- Additional interoperability rules.

This significantly reduces execution time during configuration while preserving exhaustive validations when required.

---

## Technical Challenges

One of the most complex engineering problems was designing a monitoring platform capable of supervising hundreds of independent government services simultaneously.

Each organization exposes different infrastructure, authentication mechanisms, response times, and operational behaviors.

The monitoring engine needed to remain resilient even when external systems became unavailable.

Another major challenge involved preventing monitoring executions from overwhelming the platform.

Since many public entities share similar execution schedules, validations had to be distributed intelligently instead of executing simultaneously.

Designing a scheduler capable of evaluating execution times, queuing pending validations, and executing them asynchronously became one of the core architectural components of the platform.

Supporting multiple interoperability implementations also required building flexible validation logic capable of handling optional OAuth parameters, varying authentication flows, and different API behaviors while still producing meaningful operational results for non-technical users.

Finally, translating low-level HTTP failures into understandable operational messages significantly improved the usability of the platform for technical coordinators and institutional administrators.

---

## Infrastructure

Centinela was deployed as an independent backend service within the SESAJ ecosystem.

The application runs inside Docker containers hosted on AWS EC2 instances and communicates with the Institutional API through secured internal endpoints protected by service API keys.

Continuous deployment was automated using GitHub Actions, allowing every approved change to be built and deployed with minimal manual intervention.

Monitoring data, execution history, validation results, and operational metrics are stored in a dedicated PostgreSQL database, keeping monitoring information isolated from credential management.

The infrastructure was designed so that Centinela could eventually be deployed independently from the rest of the ecosystem if monitoring demand continued to increase.

Infrastructure components include:

- AWS EC2
- PostgreSQL
- Docker
- GitHub Actions
- Nginx
- Linux
- FastAPI
- Angular

---

## Technologies

### Backend

- Python
- FastAPI
- AsyncIO
- BackgroundTasks

### Frontend

- Angular
- TypeScript

### Cloud

- AWS EC2

### Infrastructure

- Docker
- GitHub Actions
- Nginx
- Linux

### Database

- PostgreSQL

### Communication

- REST APIs
- API Gateway
- HTTPX

---

## Impact

Centinela established continuous operational monitoring for the SESAJ interoperability ecosystem.

The platform automated validation of government interoperability services, allowing technical teams to detect operational issues before they affected information exchange with the National Digital Platform.

By separating monitoring from credential management, the architecture improved security boundaries while enabling future independent scaling of monitoring workloads.

The scheduler and asynchronous execution model allowed hundreds of interoperability validations to be distributed efficiently without overwhelming either the monitoring platform or external government services.

Operational dashboards, execution history, and validation evidence significantly improved visibility into the health of every connected public entity and simplified day-to-day monitoring activities.

The platform also standardized interoperability validation, reducing manual verification efforts and providing consistent technical evidence before enabling production integrations.

---

## Lessons Learned

Centinela was the project that strengthened my understanding of distributed backend systems and large-scale operational monitoring.

Designing a scheduler capable of coordinating hundreds of recurring validations taught me that scalability depends more on workload orchestration than raw processing power.

I also learned the importance of separating responsibilities between services, allowing each component to evolve independently while maintaining clear security boundaries.

Another valuable lesson was designing software for operational users instead of developers.

Presenting technical failures as understandable operational messages greatly improved usability and reduced the time required to diagnose interoperability issues.

If I were implementing the platform today, I would preserve the overall architecture while introducing container orchestration, centralized logging, distributed tracing, metrics collection, and message queues to support even larger deployments.

Centinela represents one of the most technically challenging systems I have designed because it combines distributed monitoring, asynchronous processing, API validation, scheduling, analytics, and secure service communication into a single operational platform.