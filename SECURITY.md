# Security Policy

## Supported Versions

| Version | Supported |
| ------- | --------- |
| 1.4.x   | Yes       |
| 1.3.x   | Yes       |
| 1.2.x   | Yes       |
| < 1.2   | No        |

## Reporting a Vulnerability

Report security issues privately through
[GitHub Security Advisories](https://github.com/gianlucamazza/langchain-rag-tutorial/security/advisories/new)
(the "Security" tab of this repository).

Please do **not** open a public issue or disclose the vulnerability publicly before a fix is
released.

### What to Include

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix, if any

## Response Time

There is **no committed SLA**. The project is maintained in spare time; the notes
below are aspirational only and are not a guarantee of acknowledgement, fix, or
disclosure timing.

- We aim to acknowledge reports when we can
- Fixes are prioritized by severity and available time
- Disclosure is coordinated after a fix is released, when practical

## Security Best Practices

### API Keys

- Keep keys in environment variables or a `.env` file; never commit `.env`.
- Rotate keys regularly and immediately after any exposure.
- Use a secrets manager in production (for example AWS Secrets Manager or Azure Key Vault).

### Docker

- The image runs as a non-root user and uses a multi-stage build.
- Scan images for vulnerabilities and keep the base image (`python:3.12-slim`) updated.

### Production Deployment

- Enable HTTPS/TLS.
- Implement rate limiting, authentication and authorization.
- Restrict CORS origins.
- Monitor for suspicious activity.

See [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md#security) for implementation examples.

## Known Issues

None at this time.

## Security Updates

Security updates are announced through GitHub Security Advisories, the
[changelog](docs/CHANGELOG.md) and git tags.

---

Last updated: 2026-09-21
