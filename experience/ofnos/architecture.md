# OFNOS Architecture

## Overview

The OFNOS platform was designed as a cloud-native multi-tenant SaaS architecture capable of serving multiple wholesale distribution companies while maintaining isolated customer environments.

The architecture combines backend APIs, web applications, mobile applications, cloud infrastructure, relational databases, and Infrastructure as Code to provide a scalable distribution management platform.

Rather than deploying completely independent software projects for each customer, the platform provisions isolated infrastructure while reusing the same application architecture.

---

## Architecture Goals

The architecture was designed around the following principles:

- Multi-tenant SaaS architecture.
- Infrastructure automation.
- Independent customer environments.
- Reusable backend services.
- Shared business logic.
- Cloud-native deployment.
- Mobile and web integration.
- Scalable infrastructure.

---

## System Components

### Backend API

The backend exposes REST APIs responsible for all business operations.

Responsibilities include:

- Authentication.
- Inventory management.
- Warehouse management.
- Customer management.
- Product catalog.
- Order processing.
- Route management.
- Mobile API.

Business logic remains centralized inside backend services.

---

### Web Application

The web application provides administrative functionality for warehouse personnel and company administrators.

Responsibilities include:

- Inventory administration.
- Product management.
- Warehouse operations.
- Customer management.
- Order administration.
- Reports.

---

### Mobile Application

The Ionic application supports field operations performed by delivery personnel.

Responsibilities include:

- Order delivery.
- Route visualization.
- Customer visits.
- Delivery confirmation.

---

## Cloud Infrastructure

Every customer environment is provisioned automatically through Terraform.

Each deployment creates independent AWS infrastructure including compute, databases, storage, networking, and application services.

This approach guarantees isolation while maintaining deployment consistency across customers.

---

## Authentication

Authentication is centralized using JWT.

Both the web and mobile applications consume the same authentication services.

This provides a consistent security model across the platform.

---

## Data Ownership

Application data is stored within PostgreSQL.

Cloud resources remain isolated for every customer deployment.

Object storage is managed through Amazon S3.

---

## Infrastructure Provisioning

Infrastructure provisioning is performed through Infrastructure as Code.

Terraform automates the creation of:

- EC2 instances.
- PostgreSQL databases.
- Amazon S3 buckets.
- Networking resources.
- Security groups.
- Application infrastructure.

Automating infrastructure significantly reduced manual deployment effort while improving repeatability.

---

## Deployment Strategy

Applications are containerized using Docker.

Infrastructure provisioning is handled by Terraform.

Backend services, frontend applications, and supporting cloud resources are deployed independently while remaining part of the same customer environment.

---

## Architectural Principles

Several engineering principles guided the platform design.

- Reuse application architecture.
- Isolate customer infrastructure.
- Centralize business logic.
- Automate infrastructure provisioning.
- Minimize manual deployment.
- Design for scalability.
- Prefer Infrastructure as Code.
- Keep cloud resources reproducible.

---

## Lessons Learned

Designing both software architecture and cloud infrastructure demonstrated how closely application design and operational infrastructure are connected.

Working with Terraform reinforced the value of Infrastructure as Code, repeatable deployments, and automated provisioning.

The project also strengthened my understanding of multi-tenant SaaS architectures, cloud-native applications, backend service design, and infrastructure automation, providing practical experience in designing systems that can scale as new customers are onboarded.