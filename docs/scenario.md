# SENTINEL — Scenario Design

## Setting
SENTINEL is the internal operations platform of a company running autonomous refrigerated delivery vehicles for temperature-sensitive pharmaceuticals.

The platform combines incident reporting, vehicle telemetry, maintenance workflows, dispatch operations, and emergency controls.

## Story
A delivery driver reports an unusual refrigeration event. The report is routed to an Operations Analyst for review. The analyst's browser is trusted by the application because it is an authenticated employee session.

The challenge is designed around the idea that a seemingly harmless reporting feature can become the first link in a cross-boundary attack when browser trust and API authorization are inconsistent.

## Roles
| Role | Intended access |
|---|---|
| Driver | Create and view own incident reports |
| Operations Analyst | Review incidents and operational telemetry |
| Operations Manager | Manage maintenance workflows and operational exceptions |
| Administrator | Full administrative access |

## Vulnerability chain
- Stored XSS in an incident-report field.
- Privileged browser execution in the same origin.
- Object-level authorization weakness on vehicle telemetry.
- Function-level authorization weakness on emergency maintenance override.

## Special vehicle
VEH-7719 is seeded as a restricted vehicle associated with a sensitive maintenance event. Its data should not directly contain the final flag. The telemetry and maintenance records instead provide enough legitimate application context for a player to discover the next workflow.

## Design principles
- Real-world terminology instead of obvious admin/secret/flag naming.
- Multiple benign records to prevent the vulnerable record from looking artificial.
- Consistent identifiers across incidents, vehicles, telemetry, maintenance events, and audit records.
- No dependency on external services.
- Deterministic reset so the lab can be reproduced for CTF participants.
