# API Contract — Planned Surface

| Method | Route | Purpose | Intended issue |
|---|---|---|---|
| POST | /api/incidents | Create incident | Stored XSS input |
| GET | /api/incidents | List incidents | Normal workflow |
| GET | /api/incidents/{id} | Incident details | Normal workflow |
| GET | /api/vehicles | List vehicles | Discovery |
| GET | /api/vehicles/{vehicle_id}/telemetry | Vehicle telemetry | BOLA |
| GET | /api/maintenance/{id} | Maintenance event | Workflow discovery |
| POST | /api/maintenance/{id}/emergency-override | Emergency override | Function-level authorization |
| GET | /api/audit/events | Operational audit data | Context and realism |

## Authentication
Use server-side sessions with HttpOnly, Secure, and appropriate SameSite attributes. Do not expose session secrets to client-side JavaScript.

## Authorization
The vulnerable endpoints are intentional CTF mechanics. The final implementation must document the intended secure authorization checks in docs/defensive-design.md.
