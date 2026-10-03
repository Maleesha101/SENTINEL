# Defensive Design Notes

SENTINEL is intentionally vulnerable, but every vulnerability should have an explicit secure-design counterpart.

## Stored XSS
- Encode output for its exact rendering context.
- Prefer text rendering APIs when rich HTML is unnecessary.
- Sanitize HTML with a well-maintained allowlist when HTML is a legitimate feature.
- Add CSP as defense in depth.

## Object authorization
- Authorize every object access server-side.
- Do not assume that possession of an identifier implies access.
- Scope database queries to the authenticated principal or permitted organization.

## Function authorization
- Enforce action-level permissions on every sensitive operation.
- Treat HTTP method and UI visibility as presentation details, not security boundaries.
- Record privileged operations in an auditable event stream.

## Browser session security
- Use HttpOnly cookies.
- Use Secure cookies in HTTPS deployments.
- Configure SameSite appropriately.
- Do not treat HttpOnly as an XSS defense; it only limits direct cookie access.
