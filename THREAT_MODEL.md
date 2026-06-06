# Threat Model

Simple threat model for the private `tawhid.ro` project. This document is public-safe and avoids private implementation details.

## Assets

- Islamic content
- Admin and deployment access
- Domain and DNS control
- Email accounts
- Contact form submissions
- User trust and reputation

## Possible Attackers

- Opportunistic web scanners looking for common vulnerabilities
- Spammers targeting contact forms
- Phishing attackers targeting admin, email, domain, or deployment accounts
- Malicious users attempting to inject scripts or misleading content
- Attackers attempting domain, DNS, or email takeover
- Scrapers or impersonators misusing project identity or content

## Possible Risks

- Secret leakage through source control, logs, or deployment settings
- XSS through rendered content, imported content, unsafe links, or embedded media
- Contact form spam, abuse, or personal data exposure
- Dependency vulnerabilities in web framework or supporting packages
- Unauthorized deployment or admin access
- Domain/DNS compromise or misconfiguration
- Email spoofing or phishing using project identity
- Loss or corruption of Islamic content
- Reputational damage caused by incorrect content, defacement, or impersonation

## Mitigations

- Keep production source code and secrets private.
- Store secrets in environment-specific configuration, not committed files.
- Review dependencies and update security patches.
- Treat rendered content and external media as security-sensitive.
- Validate contact form inputs and add spam protection where needed.
- Use security headers appropriate for the deployment.
- Protect admin, hosting, email, and DNS accounts with strong passwords and MFA.
- Keep domain and DNS ownership records current.
- Back up content and important configuration.
- Review public content carefully before publishing.

## Future Improvements

- TODO: Document the exact content rendering and sanitization flow.
- TODO: Confirm current contact form spam controls.
- TODO: Confirm current backup and recovery process.
- TODO: Confirm current DNS and email security posture.
- TODO: Add a public-safe architecture diagram.
- TODO: Revisit this threat model after any authentication, admin, CMS, or form changes.
