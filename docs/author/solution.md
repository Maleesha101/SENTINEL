# SENTINEL — Author Walkthrough

> AUTHOR ONLY — DO NOT LINK FROM PLAYER DOCUMENTATION

## Intended chain
1. Submit a crafted incident report containing executable content.
2. Wait for the Operations Review Bot to open the report.
3. The content executes in the analyst's authenticated origin.
4. Use same-origin requests from that browser context to inspect accessible API behavior.
5. Abuse the intended object-level authorization weakness to access VEH-7719 telemetry.
6. Follow the maintenance event reference to the emergency workflow.
7. Invoke the intentionally under-protected emergency override action.
8. The server records the completed challenge state and returns the flag.

## Authoring constraints
The exact payload, seeded credentials, endpoint implementation, and flag value belong here rather than in player documentation.

## Validation
The complete chain must work from a clean reset using only the player-visible application and normal browser tooling. A direct database modification must not be required.
