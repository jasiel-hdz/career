# Farmacias del Ahorro Interactive Retail Platform

## Overview

The Farmacias del Ahorro Interactive Retail Platform is a retail analytics solution designed to collect customer interaction data from intelligent product displays installed across pharmacies.

The platform combines interactive experiences, computer vision, offline data synchronization, inventory analytics, and operational dashboards to help brands understand customer behavior and product engagement.

Several types of smart displays were deployed, each providing different interaction capabilities such as touch screens, proximity sensors, product detection, and customer analytics.

---

## Business Context

Traditional retail displays provide little information about customer interaction and purchasing behavior.

The objective of the project was to transform physical product displays into intelligent devices capable of collecting interaction metrics, analyzing customer demographics, and synchronizing operational data with a centralized analytics platform.

Because many displays operated with unstable or unavailable internet connectivity, the platform also required a reliable offline synchronization mechanism.

---

## Product Overview

The platform provides:

- Interactive product experiences.
- Customer analytics.
- Computer vision integration.
- Product interaction tracking.
- Inventory interaction metrics.
- Offline data collection.
- Batch synchronization.
- Operational dashboards.
- Product management.
- Smart display administration.

Each smart display generated operational events that were later synchronized with the central backend.

---

## Architecture

The solution consists of two primary components.

Interactive applications running locally on smart displays.

A centralized dashboard responsible for collecting analytics, managing products, and presenting operational reports.

Each display operates independently and continues collecting events even when internet connectivity is unavailable.

Once connectivity is restored, locally stored events are synchronized automatically with the backend.

---

## My Contributions

My responsibilities included:

- Developing frontend and backend components.
- Building the operational dashboard.
- Developing product and display management modules.
- Refactoring multiple interactive display applications.
- Designing and implementing an offline-first synchronization architecture.
- Implementing a state machine for device synchronization.
- Designing batch synchronization workflows.
- Improving application reliability under unstable network conditions.
- Supporting production deployments.

---

## Engineering Decisions

### Offline-First Architecture

One of the primary engineering decisions was allowing every interactive display to continue operating without internet connectivity.

Instead of depending on permanent network access, events are stored locally and synchronized later.

This guarantees data integrity regardless of network availability.

---

### State Machine Design

Different synchronization scenarios required deterministic behavior.

A state machine was implemented to control every synchronization phase, including offline operation, local persistence, pending synchronization, successful delivery, and failure recovery.

This significantly simplified synchronization logic while improving maintainability.

---

### Batch Synchronization

Instead of sending every event individually, collected interactions are grouped and transmitted in batches.

This reduces network overhead, improves synchronization efficiency, and minimizes server load.

---

## Technical Challenges

The most complex engineering challenge involved guaranteeing reliable synchronization while devices operated offline for extended periods.

Data could never be lost regardless of connectivity conditions.

Another challenge involved supporting multiple smart display models with different hardware capabilities while maintaining a common synchronization workflow.

Designing the synchronization state machine required carefully handling network failures, retries, local persistence, and successful recovery without creating duplicated information.

---

## Infrastructure

Interactive applications execute locally on retail devices.

The centralized platform was deployed using cloud infrastructure supporting backend services, dashboards, and analytics processing.

Infrastructure components include:

- Azure
- Docker
- Linux
- Git

---

## Technologies

### Backend

- .NET

### Frontend

- React
- Blazor

### Database

- PostgreSQL

### Infrastructure

- Azure
- Docker
- Linux

---

## Impact

The platform enabled intelligent retail displays capable of operating independently from network availability while continuously collecting customer interaction data.

Offline synchronization significantly improved system reliability by preventing information loss during connectivity interruptions.

The dashboard provided centralized visibility into customer behavior, product engagement, and operational metrics collected from multiple retail locations.

---

## Lessons Learned

This project strengthened my understanding of offline-first architectures, distributed synchronization, and resilient application design.

Designing the synchronization state machine demonstrated the importance of deterministic workflows when handling unreliable network conditions.

The experience also reinforced how software architecture directly impacts reliability in real-world deployments where internet connectivity cannot be guaranteed.