# BBVA Queue Management Platform

## Overview

The BBVA Queue Management Platform is an enterprise solution deployed across bank branches to optimize customer flow, prioritize service based on business rules, and provide operational analytics for branch managers.

The platform combines queue management, computer vision, customer prioritization, and business intelligence to improve customer experience while providing real-time operational metrics.

Interactive kiosks identify customers, assign service tickets, and direct them to the appropriate service desk based on predefined priority rules. Managers can monitor branch performance through dashboards containing customer demographics, waiting times, service duration, and operational KPIs.

---

## Business Context

BBVA serves thousands of customers every day across multiple branches.

Managing customer flow efficiently is critical for reducing waiting times, improving service quality, and optimizing employee performance.

The bank required a centralized platform capable of organizing customer queues while collecting operational data that could later be analyzed to improve branch efficiency.

Additionally, customer identification through computer vision enabled the platform to generate demographic analytics without interrupting the customer experience.

---

## Product Overview

The platform provides several capabilities:

- Customer queue management.
- Intelligent ticket assignment.
- Customer prioritization.
- Computer vision integration.
- Branch analytics dashboards.
- Waiting time metrics.
- Service time metrics.
- Customer demographic analysis.
- Branch performance reports.

The solution operates nationwide across multiple BBVA branches.

---

## Architecture

The platform follows a distributed architecture composed of several independent services.

Interactive kiosks receive customer requests and communicate with backend services responsible for ticket generation, queue management, authentication, analytics, and reporting.

Computer vision services process customer images and generate demographic information consumed by analytics dashboards.

Operational dashboards aggregate data from multiple branches, allowing managers to monitor customer flow and employee performance in real time.

---

## My Contributions

My primary responsibilities included:

- Developing backend services using FastAPI.
- Implementing business logic for queue management.
- Developing frontend improvements.
- Integrating Amazon Cognito authentication.
- Designing and implementing user synchronization scripts.
- Supporting cloud integrations.
- Participating in production deployments.
- Collaborating with frontend and backend teams to deliver new platform capabilities.

---

## Engineering Decisions

### Amazon Cognito Integration

Instead of implementing a custom authentication system, Amazon Cognito was adopted to centralize user authentication and authorization.

To simplify user onboarding, I developed synchronization scripts capable of automatically importing users into Cognito while maintaining consistency with existing application data.

---

### Backend Service Design

Business logic remained isolated from presentation components, allowing frontend applications to evolve independently while keeping backend services reusable across different platform modules.

---

## Technical Challenges

One of the most challenging tasks involved integrating Amazon Cognito with the existing application.

The synchronization process required mapping existing users into Cognito while preserving authentication consistency and minimizing operational disruption.

Another challenge involved maintaining compatibility between multiple backend services and frontend applications deployed across numerous bank branches.

---

## Infrastructure

The solution was deployed using cloud infrastructure already maintained by the organization.

My participation included deployment support, backend configuration, authentication integration, and production validation.

Infrastructure components included:

- AWS
- Amazon Cognito
- Docker
- Linux
- Git

---

## Technologies

### Backend

- Python
- FastAPI

### Frontend

- Next.js
- React

### Cloud

- AWS
- Amazon Cognito

### Database

- PostgreSQL

### Infrastructure

- Docker
- Linux
- Git

---

## Impact

The platform improved customer flow management across BBVA branches by combining queue management, customer prioritization, and operational analytics into a unified solution.

The Cognito integration simplified authentication management while improving user administration through automated synchronization processes.

The analytics dashboards provided branch managers with valuable operational insights, enabling data-driven decisions to improve customer service.

---

## Lessons Learned

This project strengthened my understanding of enterprise authentication systems and cloud identity management.

Working with Amazon Cognito taught me how authentication platforms integrate with existing enterprise applications while maintaining scalability and security.

The project also reinforced the importance of separating business logic from authentication concerns, making enterprise applications easier to maintain and extend.