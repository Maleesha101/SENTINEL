# Architecture

## Planned topology
Browser → Nginx → Web application → PostgreSQL

A separate browser-worker container will simulate the authenticated Operations Review Bot.

## Components

### Web application
Responsible for authentication, incident reports, dashboards, telemetry, maintenance workflows, and the challenge flag condition.

### PostgreSQL
Stores users, roles, incidents, vehicles, telemetry, maintenance events, audit events, and challenge state.

### Nginx
Provides a single player-facing origin and reverse-proxies application routes.

### Operations Review Bot
A controlled Playwright worker that periodically signs in as an Operations Analyst and opens pending incidents. It must:
- run inside Docker;
- have access only to the SENTINEL origin;
- use a seeded analyst account;
- produce deterministic logs;
- avoid arbitrary internet access.

## Trust boundaries
1. Player-controlled browser → public application.
2. Driver-submitted incident content → persistent database.
3. Stored incident content → privileged employee browser.
4. Privileged browser → authenticated internal API.
5. API object identifiers → authorization layer.
6. Maintenance workflow → privileged operational action.

## Planned deployment
Use Docker Compose for local execution. The initial scaffold intentionally contains no production deployment configuration and no real credentials.
