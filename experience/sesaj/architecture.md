# SESAJ Architecture

## Overview

The SESAJ interoperability ecosystem was designed as a distributed platform composed of multiple independent services, each responsible for a specific business domain.

Rather than concentrating every responsibility into a single backend application, the platform separates authentication, credential management, interoperability operations, and monitoring into independent services that communicate through well-defined APIs.

This architecture improves security, maintainability, and future scalability while allowing each service to evolve independently.

---

## Architecture Goals

The architecture was designed around the following principles:

- Single responsibility for every service.
- Security-first design.
- Independent scalability.
- Clear ownership of business data.
- Centralized authentication.
- Secure service-to-service communication.
- Operational simplicity.
- Future extensibility.

---

## System Components

The ecosystem consists of three primary applications.

### Bóveda Gateway

Acts as the single entry point for institutional users.

Responsibilities include:

- Microsoft OAuth authentication.
- User session management.
- Role-based authorization.
- Frontend hosting.
- Request proxying.
- API key injection.

The gateway never contains business logic.

---

### Institutional API

The Institutional API owns all business operations related to Bóveda.

Responsibilities include:

- Secret management.
- Organization management.
- Credential sharing.
- Interconnection management.
- Attachments.
- Audit logs.
- Credential resolution.
- Electronic signature.
- Proxying requests to Centinela.

Sensitive information is stored only within this service.

---

### Centinela

Centinela is responsible exclusively for monitoring and interoperability validation.

Responsibilities include:

- Health monitoring.
- Functional validation.
- Interoperability testing.
- Scheduler execution.
- Monitoring history.
- Dashboards.
- Availability metrics.

Centinela never stores institutional credentials.

---

## Service Communication

Users always interact with the Bóveda Gateway.

The gateway authenticates users and forwards requests to the Institutional API.

Whenever monitoring functionality is required, the Institutional API proxies requests to Centinela.

When Centinela needs credentials to validate an interoperability endpoint, it securely requests credential resolution from the Institutional API.

This design establishes a single owner for sensitive information while keeping monitoring isolated.

---

## Security Model

Security was one of the primary architectural concerns.

Several decisions were made to minimize risk.

- Credentials are encrypted before storage.
- Encryption keys remain outside the database.
- Monitoring services never persist credentials.
- API keys secure service-to-service communication.
- Microsoft OAuth authenticates institutional users.
- RBAC controls access to platform functionality.
- Audit logs record sensitive operations.

---

## Data Ownership

Each service owns its own database.

This prevents tight coupling while allowing each service to evolve independently.

### Bóveda Database

Stores:

- Organizations
- Encrypted secrets
- Interconnections
- Audit logs
- Attachments
- API Keys

---

### Gateway Database

Stores:

- Users
- Roles
- Permissions

---

### Centinela Database

Stores:

- Monitors
- Validation runs
- Dashboards
- Dependencies
- Operational metrics

No credentials are stored within Centinela.

---

## Scalability Strategy

The platform was intentionally designed to support future growth.

As the number of connected public entities increases, monitoring workloads can be scaled independently without affecting credential management.

Because services are isolated, individual components can be deployed separately if required.

This reduces operational risk while simplifying future infrastructure evolution.

---

## Deployment Strategy

Applications are deployed independently using Docker containers running on AWS EC2.

Continuous deployment is performed through GitHub Actions.

Nginx serves as the reverse proxy and frontend host.

Supporting documents are stored in Amazon S3.

This deployment strategy keeps services independent while maintaining a simple operational model.

---

## Architectural Principles

Several principles guided the overall design.

- Keep sensitive data isolated.
- Avoid duplicated business logic.
- Minimize coupling between services.
- Define clear service ownership.
- Secure internal communication.
- Prefer asynchronous processing for long-running operations.
- Build services that can evolve independently.
- Design infrastructure that supports future scalability without requiring major architectural changes.

---

## Lessons Learned

Designing the architecture of the SESAJ ecosystem strengthened my understanding of distributed systems, secure service communication, and long-term software maintainability.

The project reinforced the importance of separating business domains early, establishing clear ownership boundaries, and treating security as an architectural concern rather than an implementation detail.

It also demonstrated how thoughtful architectural decisions can significantly simplify future development while reducing operational complexity.