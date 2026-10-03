# Challenge Attack Path

This document describes the intended learning sequence without providing a ready-to-copy exploit payload.

## Stage 1 — Find the input
Locate the incident-report workflow and identify where attacker-controlled content is accepted and later displayed to an employee.

## Stage 2 — Establish browser execution
Determine the rendering context and demonstrate that stored content can execute in the Operations Analyst's browser. The challenge should reward understanding of context and browser behavior rather than a generic popup.

## Stage 3 — Use the authenticated origin
The analyst session uses an HttpOnly cookie. The intended route therefore requires same-origin browser interaction rather than direct cookie theft.

## Stage 4 — Discover internal API behavior
Use application behavior, browser developer tools, source inspection, or normal UI actions to identify relevant API routes.

## Stage 5 — Cross the object boundary
The telemetry API contains an object-level authorization weakness. A player should be able to reason from legitimate vehicle identifiers to a restricted vehicle record.

## Stage 6 — Discover the operational workflow
The restricted telemetry should point toward a maintenance event or operational exception. The next endpoint should be discoverable from normal application artifacts rather than hidden through obscurity.

## Stage 7 — Cross the function boundary
The emergency maintenance endpoint incorrectly trusts the caller's authenticated role. The final challenge state is reached only when the restricted maintenance action is successfully invoked.

## Stage 8 — Flag
The application reveals the flag only after the complete state transition. The flag must not be present in incident text, telemetry, HTML comments, JavaScript bundles, or static files.
