# Bóveda

## Overview

Bóveda is the secure credential management platform that serves as the operational foundation of the SESAJ interoperability ecosystem.

The platform centralizes the administration of institutional credentials, organizations, interoperability configurations, digital documents, electronic signatures, and audit information required to operate integrations between government entities and the National Digital Platform (PDN).

Rather than functioning as a traditional password vault, Bóveda acts as the operational gateway through which administrators configure organizations, manage secure credentials, establish interoperability settings, and access the different applications that compose the ecosystem.

The platform was designed with security as its primary concern, ensuring that sensitive credentials remain encrypted, access is fully auditable, and confidential information is never exposed directly to external organizations or client applications.

---

## Business Context

SESAJ coordinates the technical interoperability between multiple public entities that exchange information with the National Digital Platform (PDN).

Each public entity exposes its own services, authentication endpoints and infrastructure, requiring SESAJ to securely manage hundreds of institutional credentials and interoperability configurations.

Before Bóveda, credentials were commonly exchanged through email or manual communication channels, creating significant operational and security risks. There was no centralized mechanism to control who accessed credentials, when they were accessed, or whether they had already been shared with external organizations.

The growing number of public entities, integrations and credentials required a centralized platform capable of securing institutional information while providing operational visibility and complete traceability.

---

## Product Overview

Bóveda provides a secure environment where institutional secrets are centrally managed, encrypted, audited and shared using temporary access mechanisms instead of exposing usernames and passwords directly.

The platform allows administrators to:

- Manage organizations participating in interoperability.
- Register and securely store institutional credentials.
- Share secrets using temporary secure links with expiration policies.
- Configure interoperability settings.
- Manage users and permissions.
- Upload supporting documents.
- Audit every relevant operation performed within the platform.
- Provide secure access to the monitoring platform (Centinela).

Bóveda also serves as the unified entry point for the ecosystem, allowing users to access both credential management and interoperability monitoring through a single application.

---

## Architecture

The platform was designed following a service-oriented architecture where each component owns a specific business responsibility.

The ecosystem is composed of three primary services:

- Bóveda Gateway
- Institutional API
- Centinela Monitoring Service

Users interact only with the Bóveda Gateway.

The gateway authenticates users through Microsoft OAuth, validates local permissions, injects server-side credentials, and proxies requests to the institutional API.

The institutional API owns the core business logic, including organizations, encrypted secrets, secret sharing, interoperability management, audit logs, attachments and integrations.

Centinela operates as an independent monitoring service responsible for interoperability validation and continuous health monitoring. It never stores sensitive credentials and requests them securely from the institutional API only when required.

This separation allows each service to evolve independently while minimizing security risks and simplifying future scalability.

---

## My Contributions

I participated in the evolution of the SESAJ interoperability ecosystem, taking ownership of both architecture and implementation.

My Contributions included:

- Designing the microservice architecture adopted by the platform.
- Designing REST APIs and service contracts.
- Defining communication between Bóveda, the Institutional API and Centinela.
- Designing relational database models.
- Implementing backend services using FastAPI.
- Developing Angular frontend modules.
- Implementing secure credential management.
- Designing encrypted secret storage.
- Building controlled secret sharing workflows.
- Developing interoperability management features.
- Implementing institutional authentication using Microsoft OAuth.
- Designing role-based access control.
- Integrating AWS S3 for document storage.
- Implementing audit capabilities.
- Automating deployments using GitHub Actions.
- Deploying services to AWS infrastructure.
- Configuring Docker and Nginx environments.
- Participating in product architecture decisions together with stakeholders.

---

## Engineering Decisions

Several architectural decisions were made to balance security, maintainability, scalability, and operational simplicity.

### Microservice-Oriented Architecture

Instead of extending a single monolithic application, I decided to separate the ecosystem into independent services with clearly defined responsibilities.

The primary goal was to isolate sensitive operations from monitoring capabilities while allowing each service to evolve independently.

This architecture also enables future horizontal scaling if the number of connected public entities or interoperability validations grows significantly.

---

### Centralized Secret Management

Sensitive credentials are stored only within the Institutional API.

Monitoring services never persist credentials locally.

Whenever Centinela needs to validate an interoperability endpoint, it securely requests temporary credential resolution from the Institutional API.

This approach minimizes the attack surface and establishes a single source of truth for sensitive information.

---

### Credential Encryption

Institutional credentials are encrypted using MultiFernet provided by the Python cryptography library.

Encryption keys remain outside the database, ensuring that database access alone is insufficient to recover confidential information.

The objective was not only protecting stored credentials but also reducing operational risk in case of infrastructure compromise.

---

### Secure Credential Sharing

Instead of sending usernames and passwords through email, Bóveda generates temporary secure links that expose credentials only under controlled conditions.

Each share includes expiration policies and limited visibility, allowing administrators to know when credentials were accessed and from which device.

This significantly improved operational security without increasing complexity for public entities.

---

### API Gateway

The frontend never communicates directly with backend business services.

A dedicated gateway authenticates users, validates permissions, injects service credentials, and routes requests to the appropriate backend service.

This keeps internal services isolated while simplifying authentication and authorization.

---

### Microsoft Authentication

Institutional users authenticate using Microsoft OAuth because every SESAJ employee already has an official Microsoft account.

This reduced operational overhead by avoiding a custom authentication platform while integrating naturally with the institution's identity provider.

---

### Database Separation

Each service owns its own relational database.

Sensitive credential storage, user management, and monitoring data remain isolated from each other.

This reduces coupling, simplifies future migrations, and improves security boundaries between services.

---

### Unified Frontend

Although backend services were separated, I decided to maintain a single Angular application for Bóveda and Centinela.

The primary reason was to maximize component reuse, reduce development time, and maintain a consistent user experience while I was leading the implementation.

Because business logic resides almost entirely in backend services, separating frontend applications remains possible in the future without significant architectural impact.

---

## Technical Challenges

The most challenging aspect of the project was designing an architecture capable of securely supporting continuous interoperability across hundreds of public entities.

Credential management required strict isolation while still allowing monitoring services to perform automated validations without exposing sensitive information.

Designing service communication without duplicating secrets was one of the most important architectural challenges.

Another challenge was defining service boundaries that would support future growth without introducing unnecessary complexity during the first version of the platform.

Balancing security, maintainability, and development speed required multiple architectural tradeoffs throughout the project.

Finally, designing a reusable gateway capable of centralizing authentication, authorization, routing, and service communication simplified the overall ecosystem while reducing duplicated logic across services.

---

## Infrastructure

The platform was deployed on AWS using a multi-service architecture.

The frontend application is served through Nginx, while backend services run inside Docker containers hosted on EC2 instances.

Continuous deployment was automated using GitHub Actions, allowing code changes to be built and deployed with minimal manual intervention.

Application files and supporting documents are stored in Amazon S3, while PostgreSQL databases are used to isolate operational data across services.

The infrastructure was designed to keep backend services independent, making future scaling and service extraction possible without significant architectural changes.

Infrastructure components include:

- AWS EC2
- Amazon S3
- PostgreSQL
- Docker
- Nginx
- GitHub Actions
- Linux
- Microsoft OAuth
- FastAPI
- Angular

---

## Technologies

### Backend

- Python
- FastAPI

### Frontend

- Angular
- TypeScript

### Authentication

- Microsoft OAuth 2.0
- JWT
- RBAC

### Security

- MultiFernet (cryptography)
- Encrypted Secret Storage
- Temporary Secret Sharing

### Cloud

- AWS EC2
- Amazon S3

### Infrastructure

- Docker
- GitHub Actions
- Nginx
- Linux

### Database

- PostgreSQL

---

## Impact

Bóveda became the operational foundation for secure interoperability within the SESAJ ecosystem.

The platform centralized institutional credential management, replacing insecure manual processes with encrypted storage and controlled sharing mechanisms.

Its architecture established clear service boundaries between credential management and monitoring, allowing future services to evolve independently without compromising sensitive information.

By introducing encrypted secret storage, temporary credential sharing, institutional authentication, and complete auditability, the platform significantly improved operational security while simplifying day-to-day administration for technical teams.

The project also provided the architectural foundation that later enabled Centinela to perform interoperability monitoring without duplicating sensitive information.

---

## Lessons Learned

This project fundamentally changed the way I approach software architecture.

One of the biggest lessons was understanding that designing software is not only about implementing features but about defining clear responsibilities between services.

I learned the importance of separating business domains before scalability becomes a problem instead of after the platform has already grown.

Building Bóveda also reinforced the value of security-first design, where sensitive information should always have a single owner and never be duplicated across services.

Designing APIs, authentication flows, encrypted storage, deployment pipelines, and communication contracts taught me how architectural decisions affect maintainability far more than individual implementation details.

If I were starting the project today, I would preserve the same architectural principles while introducing additional infrastructure automation, centralized observability, distributed tracing, and container orchestration to support larger deployments.

Overall, Bóveda represents the project where I transitioned from implementing backend services to designing complete software platforms focused on security, scalability, and long-term maintainability.