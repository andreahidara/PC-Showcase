# Changelog

All notable changes to the **Protección Civil** operational platform are documented in this file.

The project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.2.0] — 2026-09-18
### Added
- **Real-time GPS Tracking History**: Playback of volunteer positioning traces during emergency incidents.
- **Audio Message Streaming**: Integrated instant audio notes within operational chat channels.
- **Automated Service Callouts**: Quick summons dispatch with interactive "Attending / Unavailable" responses.
- **Dynamic Chart Analytics**: Operational performance metrics using Recharts (intervention types, hours logged, response times).

### Changed
- Migrated legacy password storage to salted `bcrypt` hashes with zero downtime.
- Optimized Leaflet map rendering with marker clustering for high-density volunteer deployments.
- Upgraded server runtime to Node.js 22 LTS and Express 5.

### Security
- Added automated PIN session locking (`AutoLock`) after configurable inactivity intervals.
- Hardened rate-limiting rules across authentication and SOS endpoints.

---

## [1.1.0] — 2026-05-12
### Added
- **Fleet Management Module**: Tracking of emergency vehicle status, ITV inspections, insurances, and mileage logs.
- **Material & Inventory Tracking**: QR barcode scanning for equipment checkout and inventory audits.
- **Treasury Ledger**: Expense tracking with digital receipt attachment uploads.
- **Emergency Protocols Repository**: Searchable protocol PDF viewer for field operational procedures.

### Changed
- Standardized UI components into a custom operational dark/light theme designed for high-stress field conditions.
- Enhanced Web Push notification reliability with VAPID subscription auto-refresh.

---

## [1.0.0] — 2026-01-15
### Added
- Initial production release.
- Core PWA with React 19 and Vite.
- Real-time communication gateway via WebSockets (`ws`).
- Operational Dashboard with live active volunteer KPIs, fleet availability, and SOS button.
- Comprehensive Service Management module (interventions, status filtering, volunteer assignments).
- PostgreSQL database schema with automated migration scripts.
