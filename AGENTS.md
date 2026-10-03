# AGENTS.md — SENTINEL

## Mission
SENTINEL is a deliberately vulnerable, isolated web-security CTF laboratory. Build it as a realistic enterprise application while keeping exploitation bounded to the local lab.

## Core learning chain
1. Attacker submits an incident containing stored XSS.
2. A simulated privileged Operations employee reviews the incident.
3. The browser executes attacker-controlled JavaScript in the SENTINEL origin.
4. The attacker uses the privileged browser context to interact with authenticated internal APIs.
5. An object-level authorization weakness exposes restricted vehicle telemetry.
6. A function-level authorization weakness exposes an emergency maintenance action.
7. The final action reveals the challenge flag.

## Engineering rules
- Do not add unrelated vulnerabilities such as SQL injection, RCE, command injection, SSRF, path traversal, or JWT algorithm confusion unless explicitly required later.
- Do not make the challenge depend on stealing a session cookie. Sessions should be HttpOnly.
- Keep all application and simulated-worker traffic inside the local Docker environment.
- Preserve realistic role boundaries: Driver, Operations Analyst, Operations Manager, Administrator.
- Keep player-facing documentation free of the complete exploit chain and final flag.
- Put authoritative walkthrough details under docs/author/.
- Add automated tests for intended challenge behavior and deterministic reset/seed behavior.
- Never commit real credentials, secrets, or production endpoints.

## Documentation
- docs/scenario.md — business scenario and challenge goals.
- docs/architecture.md — planned components and trust boundaries.
- docs/attack-path.md — challenge mechanics without exploit payloads.
- docs/api-contract.md — planned API surface.
- docs/threat-model.md — security assumptions and trust boundaries.
- docs/roadmap.md — implementation phases.
- docs/author/solution.md — maintainer-only walkthrough.

## Implementation guidance
Prefer small, testable services and deterministic seed data. Any browser automation used to represent the Operations Review Bot must run headlessly inside the lab and have no arbitrary external network access.
