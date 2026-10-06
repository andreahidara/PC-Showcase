# Testing Strategy

> This document outlines the testing strategy for the Protección Civil platform.

## Philosophy

Emergency management software requires high reliability. The testing strategy focuses on:
- **API Reliability:** Ensuring the Node.js backend handles edge cases and data validation correctly.
- **Frontend Telemetry:** Utilizing Error Boundaries to catch and report UI crashes.
- **Manual QA for Hardware Sensors:** Verifying GPS location accuracy and WebSocket connection stability under varying network conditions (3G/4G/5G transitions).

## Frameworks & Tools

| Tool | Purpose |
|:--|:--|
| **Jest / Supertest** | API Endpoint validation and unit testing |
| **ESLint & Prettier** | Static code analysis and style enforcement |
| **React Error Boundaries**| Graceful degradation and error reporting on the client |
| **Vite Developer Tools** | Performance profiling for component rendering |

## Key Test Areas

### Authentication & RBAC
- Token generation, expiration handling, and refresh flows.
- Validating that restricted endpoints correctly return `403 Forbidden` for lower-tier roles.
- `AutoLock` component triggers and PIN decryption.

### Real-Time Communications
- WebSocket handshake authentication.
- Ensuring SOS alerts broadcast to all connected Coordinators instantly.
- Handling unexpected socket disconnects and automatic reconnection backoff.

### Geolocation Accuracy
- Validating the `navigator.geolocation` polling intervals.
- Throttling coordinate updates to save battery life.
- Leaflet map rendering performance with 50+ concurrent markers.

### File Uploads
- MIME type validation (rejecting `.exe` or malicious payloads when expecting `.pdf` or `.jpg`).
- Graceful failure when upload sizes exceed server configuration limits.
