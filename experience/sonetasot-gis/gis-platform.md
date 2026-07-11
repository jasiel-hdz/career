# Metropolitan GIS Platform

## Overview

The Metropolitan GIS Platform is a public web application that provides citizens, government agencies, and technical users with access to more than 500 geographic information layers covering the Guadalajara Metropolitan Area.

The platform allows users to visualize, combine, and analyze multiple geographic datasets simultaneously through an interactive map, making spatial information accessible to both technical and non-technical users.

Administrators can publish, organize, edit, and manage geographic layers while keeping application metadata synchronized with GeoServer.

---

## Business Context

Government institutions continuously generate geographic information related to transportation, urban planning, infrastructure, environment, and public services.

Managing this information requires more than simply storing map files.

Every geographic layer must remain synchronized between the business application and the GIS server responsible for publishing map services.

The platform was created to centralize geographic information while providing a reliable administration interface capable of maintaining consistency between both systems.

---

## Product Overview

The platform provides:

- Interactive metropolitan maps.
- More than 500 geographic layers.
- Layer categorization.
- Multiple layer visualization.
- Geographic layer administration.
- CRUD operations for GIS datasets.
- GeoServer synchronization.
- Public access to geographic information.

Users can overlay multiple geographic layers simultaneously to perform spatial analysis directly from the browser.

---

## Architecture

The solution follows a two-system architecture.

The Django application manages business logic, metadata, permissions, and administration.

GeoServer is responsible for publishing and rendering geographic services consumed by OpenLayers.

Whenever a geographic layer is created, updated, or deleted, both systems must remain synchronized.

To preserve consistency, backend operations coordinate changes across both platforms while rolling back completed operations if any step fails.

This prevents inconsistencies between published GIS services and application metadata.

---

## My Contributions

My responsibilities included:

- Leading the development team.
- Working directly with stakeholders and clients.
- Developing backend services using Django.
- Developing Angular frontend modules.
- Designing complete CRUD operations for geographic layers.
- Integrating Django with GeoServer.
- Implementing OpenLayers map visualization.
- Supporting multiple simultaneous geographic layers.
- Designing rollback mechanisms for synchronized operations.
- Refactoring existing modules.
- Improving user experience.
- Participating in production deployments.

---

## Engineering Decisions

### GeoServer Synchronization

GeoServer and the application database had to remain synchronized at all times.

Instead of allowing partial updates, operations were designed to behave as logical transactions.

Whenever synchronization failed, rollback mechanisms restored consistency between both systems.

---

### Rollback Strategy

Geographic information cannot become inconsistent.

Rollback procedures were implemented to guarantee that failed operations never left orphaned services or incomplete metadata.

This significantly improved platform reliability.

---

### OpenLayers Integration

OpenLayers was selected because it supports advanced GIS visualization capabilities while allowing users to overlay multiple geographic layers efficiently.

This provided a flexible interface for spatial analysis without requiring specialized GIS software.

---

### Backend-Centered GIS Operations

Business rules remained centralized inside the backend.

Frontend applications simply requested GIS operations without needing to understand GeoServer internals.

This simplified maintenance while improving system reliability.

---

## Technical Challenges

One of the most complex engineering challenges involved synchronizing two independent systems that manage different aspects of the same geographic information.

GeoServer publishes map services, while Django manages business metadata.

Maintaining consistency between both systems required carefully coordinating operations and implementing rollback procedures whenever synchronization failed.

Another challenge involved integrating OpenLayers with hundreds of geographic layers while maintaining acceptable rendering performance and a responsive user experience.

Working with GeoServer also required understanding a platform with limited documentation, making troubleshooting and implementation significantly more challenging.

---

## Infrastructure

The application was deployed using Docker containers running on Linux servers.

GeoServer operated as an independent service responsible for geographic rendering while Django handled business operations and administration.

Infrastructure components include:

- Docker
- Linux
- GeoServer
- PostgreSQL
- Git

---

## Technologies

### Backend

- Python
- Django

### Frontend

- Angular
- TypeScript
- OpenLayers

### GIS

- GeoServer

### Database

- PostgreSQL

### Infrastructure

- Docker
- Linux
- Git

---

## Impact

The platform centralized hundreds of geographic datasets into a single public application, making spatial information more accessible to government institutions and citizens.

The synchronization strategy between Django and GeoServer improved operational reliability by preventing inconsistencies between published GIS services and application metadata.

The project also improved the administration experience by providing intuitive tools for managing large numbers of geographic layers while maintaining system consistency.

---

## Lessons Learned

This project significantly strengthened my understanding of Geographic Information Systems, distributed data consistency, and transactional backend design.

Working with GeoServer taught me how to integrate specialized third-party platforms into enterprise applications while maintaining reliable synchronization.

Leading the development team also improved my communication, technical leadership, and architectural decision-making skills while working directly with stakeholders and end users.