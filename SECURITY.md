# Security Policy

## Reporting a Vulnerability

Protección Civil handles operational and emergency data, making security and data confidentiality top priorities. If you discover a security vulnerability, please report it responsibly.

### How to Report

**Do NOT open a public GitHub issue for security vulnerabilities.**

Please contact the project maintainer directly with:
1. Vulnerability description and classification
2. Reproducible steps or proof-of-concept
3. Potential operational impact
4. Suggested remediation if available

### Scope

This security policy applies to:
- The Protección Civil PWA Web Client
- The Protección Civil Node.js / Express Core Server
- Operational APIs and WebSocket gateways

### What's NOT in Scope
- This showcase repository (contains no runnable source code or credentials)
- Third-party map tile providers (OpenStreetMap / CartoDB)

---

## 🔒 Security Measures Implemented

- **Hierarchical RBAC (Role-Based Access Control)**: Granular permissions matrix distinguishing between Volunteer, Team Lead (*Jefe de Equipo*), Coordinator (*Coordinador*), and Administrator (*Administrador*).
- **Authentication & Password Protection**: Passwords salted and hashed with `bcrypt` with automatic transparent migration on authentication. Stateless sessions managed via cryptographically signed JSON Web Tokens (JWT).
- **Session Auto-Lock (`AutoLock`)**: Automatic inactivity timer locks the client UI into a PIN-protected state, preventing unauthorized access on unattended emergency operational terminals.
- **HTTP Header Hardening & Rate Limiting**: Production middleware powered by `helmet` to mitigate XSS, Clickjacking, and MIME sniffing attacks. API rate limiting throttles authentication endpoints against brute force.
- **SQL Injection Prevention**: All database queries executed through parameterized queries with PostgreSQL (`pg` connection pool).
- **CORS Policy Enforcement**: Strict cross-origin resource sharing restricted solely to approved domain whitelists and PWA clients.
- **WebSocket Gateway Authentication**: Socket connection upgrades validate user credentials before admitting clients into private operational channels and GPS broadcast channels.
- **Web Push Security**: Notification payloads encrypted using standard VAPID (*Voluntary Application Server Identification*) key pairs.
- **File Upload Isolation**: MIME type verification and sanitized file names preventing path traversal and arbitrary execution.
