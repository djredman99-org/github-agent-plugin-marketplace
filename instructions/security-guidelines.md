# Security Guidelines

These guidelines define the minimum security requirements for all code contributed to this repository. They are non-negotiable; findings that violate these guidelines will block a pull request from merging.

## Secrets and Credentials

- **Never** hardcode API keys, passwords, tokens, or any other secrets in source code.
- Store secrets in environment variables and reference them via `process.env.SECRET_NAME` (Node.js) or `os.environ["SECRET_NAME"]` (Python).
- Use a secrets manager (e.g., AWS Secrets Manager, Azure Key Vault, HashiCorp Vault) in production.
- Rotate secrets immediately if they are accidentally committed. Treat a committed secret as compromised, even if the commit is subsequently reverted or the history is rewritten.
- `.env` files must be listed in `.gitignore` and never committed.

## Input Validation and Sanitisation

- Validate all input at the boundary of the system (HTTP request, file upload, CLI argument, event payload).
- Reject invalid input early with a meaningful error response; do not attempt to "fix" malformed input.
- Use an allowlist approach where possible (e.g., accept only known-good values) rather than a denylist.
- Never construct SQL queries, shell commands, or HTML by concatenating user-supplied strings. Use parameterised queries, safe APIs, or templating engines that escape output automatically.

## Authentication and Authorisation

- Use an established authentication library (e.g., Passport.js, OAuth2, OpenID Connect). Do not roll your own auth.
- Enforce authorisation checks on every protected resource. Do not rely on the UI to hide unauthorised routes.
- Use short-lived tokens (JWTs should expire in 15–60 minutes for sensitive operations).
- Implement account lockout or rate limiting on login endpoints to prevent brute-force attacks.
- Verify that object-level permissions are checked, not just resource-type-level permissions.

## Cryptography

- Use TLS 1.2 or higher for all network communication; never fall back to plain HTTP in production.
- Use AES-256-GCM for symmetric encryption and RSA-2048+ or EC P-256+ for asymmetric operations.
- Never use MD5 or SHA-1 for security-sensitive purposes (hashing passwords, signing tokens).
- Hash passwords with bcrypt, Argon2, or scrypt. Never use a raw SHA hash for password storage.
- Use a cryptographically secure random number generator (`crypto.randomBytes` in Node.js, `secrets` in Python).

## Logging and Data Exposure

- Never log personally identifiable information (PII) such as passwords, full card numbers, or SSNs.
- Mask sensitive values in logs (e.g., show only the last 4 digits of a card number).
- Do not return full error stack traces or internal error messages to API clients in production.
- Disable verbose error pages and debug endpoints before deploying to production.

## Dependencies

- Run `npm audit` or `pip-audit` as part of CI to detect known vulnerable dependencies.
- Upgrade or replace any dependency with a **Critical** or **High** severity CVE before merging.
- Pin dependency versions in lock files (`package-lock.json`, `Pipfile.lock`) to ensure reproducible builds.
- Review the security posture of any new dependency before adding it (check for active maintenance, known issues, and licence compatibility).

## Infrastructure and Configuration

- Apply the principle of least privilege to all IAM roles, service accounts, and database users.
- Restrict CORS to the known list of trusted origins. Do not use `*` in production.
- Set a restrictive Content Security Policy (CSP) to mitigate XSS risks.
- Ensure data at rest is encrypted (use encrypted storage volumes and database encryption).
