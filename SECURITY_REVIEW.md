# Security Review Checklist

This is a practical checklist for the private `tawhid.ro` project. It is not a claim of formal audit, certification, or complete security coverage.

## Status Legend

- `Verified` - checked directly from public repository contents, public site behavior, or already confirmed configuration.
- `Needs review` - security-relevant item that still needs production review.
- `Planned` - future hardening, documentation, or process work.
- `Not applicable` - not relevant to the public docs-only case-study repository.

## Secrets and Environment Variables

- [x] `Verified` Public case-study repository contains no private source code, `.env` files, API keys, or production credentials.
- [ ] `Needs review` Confirm private production secrets are stored only in approved environment/configuration systems.
- [ ] `Needs review` Review deployment environment variables for least privilege.
- [ ] `Needs review` Rotate any secret that may have been exposed during development.
- [ ] `Planned` Document where production secrets are stored and who can access them without exposing sensitive values.

## Dependency Review

- [ ] `Needs review` Run dependency vulnerability checks before deployment.
- [ ] `Needs review` Review high-risk dependency updates before applying them.
- [ ] `Needs review` Remove unused dependencies when they are no longer needed.
- [ ] `Needs review` Keep framework and build tooling current.
- [ ] `Planned` Define regular dependency review schedule.

## XSS Risk

- [ ] `Needs review` Review rendered HTML, Markdown, imported content, and embedded media handling.
- [ ] `Needs review` Avoid unsafe HTML rendering unless sanitization is verified.
- [ ] `Needs review` Confirm user-controlled content cannot inject scripts.
- [ ] `Needs review` Review external image and link handling.
- [ ] `Planned` Document the exact sanitization and content rendering path.

## Form Spam Protection

- [ ] `Needs review` Review contact form abuse and spam risk.
- [ ] `Needs review` Confirm rate limiting, CAPTCHA, honeypot, or equivalent controls where needed.
- [ ] `Needs review` Validate and normalize submitted fields server-side.
- [ ] `Needs review` Avoid exposing internal email addresses unnecessarily.
- [ ] `Planned` Document current production form spam controls.

## Security Headers

- [x] `Verified` Security-header configuration has been identified in the private project configuration.
- [ ] `Needs review` Verify final production response headers after deployment.
- [x] `Verified` `Strict-Transport-Security` is present in the reviewed configuration.
- [x] `Verified` `X-Frame-Options` is present in the reviewed configuration.
- [x] `Verified` `Referrer-Policy` is present in the reviewed configuration.
- [x] `Verified` `Permissions-Policy` is present in the reviewed configuration.
- [ ] `Planned` Review whether a Content Security Policy should be added or tightened.

## Authentication and Admin Risks

- [ ] `Needs review` Identify all admin, deployment, CMS, email, DNS, and hosting accounts.
- [ ] `Needs review` Require strong unique passwords.
- [ ] `Needs review` Enable MFA wherever supported.
- [ ] `Needs review` Limit admin access to required users only.
- [ ] `Needs review` Review recovery email and account recovery settings.
- [ ] `Needs review` Document whether the private project has any public admin or authentication surface.
- [x] `Not applicable` The public case-study repository has no runtime authentication surface.

## Privacy Considerations

- [x] `Verified` Public case-study repository contains no contact submissions, analytics data, or personal user data.
- [ ] `Needs review` Identify personal data collected through contact forms or email.
- [ ] `Needs review` Minimize collected data.
- [ ] `Needs review` Avoid storing unnecessary contact submissions.
- [ ] `Needs review` Document how submissions are handled and retained.
- [ ] `Needs review` Review analytics, logging, and third-party services for privacy impact.
- [ ] `Planned` Confirm privacy policy coverage for current data collection.

## Backup and Recovery

- [ ] `Needs review` Identify what must be backed up: content, configuration, deployment settings, DNS records, and documentation.
- [ ] `Needs review` Confirm backups are stored separately from the main project workspace.
- [ ] `Needs review` Test recovery steps periodically.
- [ ] `Needs review` Keep a record of domain, hosting, and email recovery procedures.
- [ ] `Planned` Define recovery time expectations for the project.

## DNS and Email Security

- [ ] `Needs review` Protect domain registrar account with MFA.
- [ ] `Needs review` Review DNS records for unnecessary exposure.
- [ ] `Needs review` Confirm email sending domain configuration where applicable.
- [ ] `Needs review` Configure SPF, DKIM, and DMARC if project email is used.
- [ ] `Needs review` Monitor domain renewal status.
- [ ] `Planned` Document current DNS/email provider setup without exposing sensitive values.

## Deployment Security

- [ ] `Needs review` Restrict deployment access to trusted accounts.
- [ ] `Needs review` Use separate production secrets from local development secrets.
- [ ] `Needs review` Review build logs for accidental secret exposure.
- [x] `Verified` Canonical domain and redirect behavior were reviewed in project configuration.
- [ ] `Needs review` Review preview deployment exposure if previews are enabled.
- [ ] `Planned` Confirm deployment provider and production access controls.
