# JamSocial_SecurityAudit
Storage for work related to the security audit of Jam Social conducted by team olive in CSB435



# JamSocial | Host Memorable Events

## Project Scope: API and Front-End Security & Audit

**Objective Timeline:** May 5th – June 20th, 2025

Build on our existing project with the following key milestones: merging the mailing system into the main application, implementing secure coding practices, enhancing system observability and documentation, employing cryptographic solutions, developing robust error logging, adopting security best practices, and backfilling encryption for existing data.

## Project Components

### 1. Mailing System Integration
- Merge the mailing platform with the main project codebase.
- Ensure data integrity and security during integration.
- Validate user input and sanitize data going into emails.
- Implement rate-limiting and abuse protection.

### 2. Front-End Security & QA
- Audit checklist from Arcjet: https://blog.arcjet.com/next-js-security-checklist/
- Validate and sanitize all form inputs.
- Enforce proper use of React event handlers (avoid unsafe inline event handlers).
- Test protected routes to ensure only authorized access.
- Implement client-side route guards and role-based rendering.

### 3. API Endpoint & Utility Audits
- Validate all API inputs (e.g., Joi, Zod).
- Set request size limits to prevent abuse (e.g., `express.json({ limit: '100kb' })`).
- Escape HTML in all API outputs to prevent XSS attacks.
- Audit and remove deprecated or unused API routes.
- Minimize response payloads to only essential data.
- Implement Helmet middleware for HTTP headers.
- Follow OWASP Node.js Cheat Sheet.

### 4. Authentication & Cryptography
- Audit existing login and token generation logic.
- Upgrade to secure cryptographic token handling (e.g., `crypto.randomBytes`, `bcrypt`, `jwt` with RS256).
- Address known login vulnerabilities.
- Enable session expiration and token revocation workflows.

### 5. Testing & Quality Assurance
- Unit test all backend endpoints and utility functions.
- Test for edge cases, rate limits, and malformed inputs.
- Ensure test coverage for all user roles and protected actions.

### 6. Documentation
- Create developer-friendly documentation for all API endpoints and utilities.
- Include:
  - Input/Output contracts
  - Status code expectations
  - Common error responses
  - Security considerations

### 7. Secure Data Management
- Enhance data models with strict validation (e.g., `email`, `name`, etc).
- Normalize inputs using `trim()`, `toLowerCase()`, etc.
- Encrypt sensitive data (e.g., email, name, tokens) at rest and in transit.
- Backfill encryption on existing records.

### 8. Error Logging Improvements
- Expand current logging to capture detailed stack traces, metadata, and correlation IDs.
- Differentiate logs for `4xx`, `5xx`, and handled edge cases.
- Integrate with monitoring tools (e.g., Sentry, LogRocket, or self-hosted solutions).

### 9. Best Practices & Hardening
Implement the following security practices:
- **HTTP Headers:**
  - `CORS`, `Content-Security-Policy`, `X-XSS-Protection`, `X-Frame-Options`, `X-Content-Type-Options`, `Strict-Transport-Security`, `X-Permitted-Cross-Domain-Policies`
- **Rate Limiting:** 
  - Request caps per IP per route.
- **Header Scrubbing:** 
  - Hide `X-Powered-By` and remove stack traces from production responses.
- **Sanitization:** 
  - Use `dompurify` or similar on dynamic DOM content.
- **CSRF Protection:** 
  - Add CSRF tokens on sensitive actions.
- **Dependency Audits:** 
  - Run `npm audit` and address critical vulnerabilities.
