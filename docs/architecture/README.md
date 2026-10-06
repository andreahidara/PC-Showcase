# Protección Civil Showcase — Architecture Documentation

This directory provides insights into the architectural decisions that power the Protección Civil platform.

## Overview

The platform is designed around a traditional **Client-Server Architecture** optimized for real-time mobile usage in low-connectivity emergency environments.

### Core Architecture Components

| Component | Technology | Responsibility |
|:--|:--|:--|
| **Frontend Client** | React 19 (PWA) | Responsive UI, local state management, offline caching via Service Workers, browser-based GPS tracking. |
| **API Gateway** | Node.js + Express 5 | RESTful endpoints for CRUD operations, JWT validation, payload sanitization. |
| **Real-time Engine** | WebSocket (`ws`) | Bidirectional full-duplex communication for SOS alerts, chat, and live map tracking. |
| **Persistence Layer**| PostgreSQL (`pg`) | Relational data integrity, schema enforcement, and ACID transactions. |

### Key Design Decisions

#### 1. Progressive Web App (PWA)
Chosen over native development to ensure immediate access across Android, iOS, and Desktop web browsers without app store approval delays. The PWA manifests allow for "Add to Homescreen" functionality, granting a native-like full-screen experience for field volunteers.

#### 2. Native WebSockets over Polling
Emergency operations require sub-second latency for SOS alerts and volunteer geotracking. The platform uses native `ws` WebSockets to maintain persistent connections, drastically reducing HTTP overhead and battery consumption compared to short-polling.

#### 3. Component-Level Authorization (RBAC)
Instead of monolithic authorization, permissions are checked at the component level. UI elements (like the "New Service" button) silently unmount for unauthorized roles, reducing visual clutter and preventing unauthorized interaction before the API even receives a request.

#### 4. PostgreSQL Relational Model
A strict relational schema guarantees that emergency interventions are properly linked to assigned vehicles, volunteers, and material inventory. This ensures that a vehicle cannot be double-booked or a volunteer assigned to overlapping shifts.

#### 5. JWT Stateless Authentication
To support scale and rapid reconnects on cellular networks, the server uses stateless JSON Web Tokens. The JWT contains the user's role and identity, avoiding a database hit on every secured route while remaining highly secure.

## Diagrams

Architecture diagrams and sequence flows are rendered directly in the [Main README](../../README.md) using Mermaid syntax.
