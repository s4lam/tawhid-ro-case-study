# Security Review Checklist

This is a practical checklist for the private `tawhid.ro` project. It is not a claim of formal audit, certification, or complete security coverage.

## Secrets and Environment Variables

- [ ] Confirm no secrets are committed to source control.
- [ ] Confirm `.env` files are excluded from the private repository.
- [ ] Review deployment environment variables for least privilege.
- [ ] Rotate any secret that may have been exposed during development.
- [ ] TODO: Document where production secrets are stored and who can access them.

## Dependency Review

- [ ] Run dependency vulnerability checks before deployment.
- [ ] Review high-risk dependency updates before applying them.
- [ ] Remove unused dependencies when they are no longer needed.
- [ ] Keep framework and build tooling current.
- [ ] TODO: Define regular dependency review schedule.

## XSS Risk

- [ ] Review any rendered HTML, Markdown, imported content, or embedded media handling.
- [ ] Avoid unsafe HTML rendering unless sanitization is verified.
- [ ] Confirm user-controlled content cannot inject scripts.
- [ ] Review external image and link handling.
- [ ] TODO: Document the exact sanitization/content rendering path.

## Form Spam Protection

- [ ] Review contact form abuse and spam risk.
- [ ] Add rate limiting, CAPTCHA, honeypot, or equivalent controls where needed.
- [ ] Validate and normalize submitted fields server-side.
- [ ] Avoid exposing internal email addresses unnecessarily.
- [ ] TODO: Confirm current production form spam controls.

## Security Headers

- [ ] Review HTTP security headers in deployment output.
- [ ] Confirm `Strict-Transport-Security` is appropriate for the final domain setup.
- [ ] Confirm `X-Frame-Options` or equivalent clickjacking protection.
- [ ] Confirm `Referrer-Policy`.
- [ ] Confirm `Permissions-Policy`.
- [ ] TODO: Review whether a Content Security Policy should be added or tightened.

## Authentication and Admin Risks

- [ ] Identify all admin, deployment, CMS, email, DNS, and hosting accounts.
- [ ] Require strong unique passwords.
- [ ] Enable MFA wherever supported.
- [ ] Limit admin access to required users only.
- [ ] Review recovery email and account recovery settings.
- [ ] TODO: Document whether the project has any public admin/authentication surface.

## Privacy Considerations

- [ ] Identify personal data collected through contact forms or email.
- [ ] Minimize collected data.
- [ ] Avoid storing unnecessary contact submissions.
- [ ] Document how submissions are handled and retained.
- [ ] Review analytics, logging, and third-party services for privacy impact.
- [ ] TODO: Confirm privacy policy coverage for current data collection.

## Backup and Recovery

- [ ] Identify what must be backed up: content, configuration, deployment settings, DNS records, and documentation.
- [ ] Confirm backups are stored separately from the main project workspace.
- [ ] Test recovery steps periodically.
- [ ] Keep a record of domain, hosting, and email recovery procedures.
- [ ] TODO: Define recovery time expectations for the project.

## DNS and Email Security

- [ ] Protect domain registrar account with MFA.
- [ ] Review DNS records for unnecessary exposure.
- [ ] Confirm email sending domain configuration where applicable.
- [ ] Configure SPF, DKIM, and DMARC if project email is used.
- [ ] Monitor domain renewal status.
- [ ] TODO: Document current DNS/email provider setup without exposing sensitive values.

## Deployment Security

- [ ] Restrict deployment access to trusted accounts.
- [ ] Use separate production secrets from local development secrets.
- [ ] Review build logs for accidental secret exposure.
- [ ] Confirm production redirects and canonical domain behavior.
- [ ] Review preview deployment exposure if previews are enabled.
- [ ] TODO: Confirm deployment provider and production access controls.
