# Threat Model

## Assets
- Vehicle telemetry
- Pharmaceutical delivery metadata
- Maintenance records
- Emergency operational controls
- Employee session context
- Challenge flag

## Actors
- Untrusted external submitter
- Authenticated Driver
- Authenticated Operations Analyst
- Authenticated Operations Manager
- Administrator

## Key trust assumptions
The application incorrectly assumes that authenticated browser context and API authorization are sufficient substitutes for explicit object and function authorization. SENTINEL intentionally violates these assumptions at specific challenge points.

## Threats represented
- Stored script execution through persisted untrusted content.
- Privileged browser abuse through same-origin requests.
- Insecure direct object reference / broken object-level authorization.
- Broken function-level authorization on a sensitive operational action.

## Out of scope
SQL injection, command injection, SSRF, RCE, deserialization, filesystem attacks, credential stuffing, external network attacks, and attacks against real infrastructure.
