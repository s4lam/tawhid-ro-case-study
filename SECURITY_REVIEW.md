# Security Review Checklist

This is a practical checklist for the private `tawhid.ro` project and the public case-study repository. It is not a claim of formal audit, certification, penetration testing, or complete security coverage.

Last verification pass: 2026-06-07.

## Status Legend

- `Verified` - checked directly from repository contents, public site behavior, DNS records, or local audit output.
- `Needs review` - security-relevant item with incomplete evidence, failed check, or owner/account access requirement.
- `Planned` - future hardening, documentation, or process work.
- `Not applicable` - not relevant to the public docs-only case-study repository.

## Verification Summary

- [x] `Verified` Public case-study repo contains documentation and screenshots only.
- [x] `Verified` Current private project tracked tree has no committed production `.env` files or detected secret-pattern hits.
- [x] `Verified` Public response headers identify the production host as Vercel.
- [ ] `Needs review` Private project dependency audit found known vulnerabilities and must be remediated or risk-accepted.
- [ ] `Needs review` XSS review is not complete because multiple `dangerouslySetInnerHTML` and `innerHTML` surfaces exist.
- [ ] `Needs review` DNS/email setup needs cleanup because `_dmarc.tawhid.ro` returned multiple DMARC TXT records.
- [ ] `Needs review` Account-level controls such as MFA, registrar security, hosting access, backups, and secret storage require owner-side verification.

## Secrets and Environment Variables

- [x] `Verified` Public case-study repository contains no private source code, `.env` files, API keys, or production credentials.
- [x] `Verified` Current private project tracked tree contains only `.env.example` templates, not production `.env` files.
- [x] `Verified` Current private project tracked tree returned no detected secret-pattern hits for common API key, token, JWT, AWS key, or private-key patterns.
- [ ] `Needs review` Confirm private production secrets are stored only in approved environment/configuration systems.
- [ ] `Needs review` Review deployment environment variables for least privilege.
- [ ] `Needs review` Rotate any secret that may have been exposed during development.
- [ ] `Planned` Document where production secrets are stored and who can access them without exposing sensitive values.

## Dependency Review

- [ ] `Needs review` `npm audit --json` found 15 vulnerabilities: 4 low, 7 moderate, 4 high, 0 critical.
- [ ] `Needs review` `npm audit --omit=dev --json` still found 2 moderate production dependency vulnerabilities: `next` and `postcss`.
- [ ] `Needs review` Vulnerable packages reported include `next`, `postcss`, `qs`, `tmp`, `uuid`, `inquirer`, and Netlify/Stackbit-related packages.
- [x] `Verified` Private project has validation scripts available, including `lint`, `typecheck`, and `verify:seo`.
- [ ] `Needs review` Review high-risk dependency updates before applying them.
- [ ] `Needs review` Remove unused dependencies when they are no longer needed.
- [ ] `Planned` Define a regular dependency review schedule.

## XSS Risk

- [ ] `Needs review` Static scan found many `dangerouslySetInnerHTML` usages and some `.innerHTML` usage.
- [ ] `Needs review` Confirm each rendered HTML, Markdown, imported content, and embedded media path is trusted or sanitized.
- [ ] `Needs review` Confirm user-controlled content cannot inject scripts.
- [ ] `Needs review` Review external image and link handling.
- [ ] `Planned` Document the exact sanitization and content rendering path.
- [ ] `Planned` Review whether a Content Security Policy should be added or tightened.

## Form Spam Protection

- [x] `Verified` Contact API route has POST handling, validation, rate-limit logic, CAPTCHA-related checks, environment-variable usage, and email-send logic.
- [x] `Verified` Newsletter subscribe API route has POST handling, validation, rate-limit logic, environment-variable usage, and email-send logic.
- [ ] `Needs review` Newsletter subscribe route did not show CAPTCHA-related checks in the static scan.
- [ ] `Needs review` Honeypot controls were not detected in the scanned form/API code.
- [ ] `Needs review` Review public email exposure and whether any internal address is unnecessarily exposed.
- [ ] `Planned` Document current production form spam controls and operational monitoring.

## Security Headers

- [x] `Verified` Public homepage returns `Strict-Transport-Security`.
- [x] `Verified` Public homepage returns `X-Frame-Options`.
- [x] `Verified` Public homepage returns `Referrer-Policy`.
- [x] `Verified` Public homepage returns `Permissions-Policy`.
- [x] `Verified` Public homepage returns `X-Content-Type-Options`.
- [x] `Verified` Representative article page returns the same checked headers.
- [x] `Verified` Public `/admin` final response returns the checked headers after redirect.
- [ ] `Needs review` Public responses did not return `Content-Security-Policy`.

## Authentication and Admin Risks

- [x] `Verified` Private project contains a public admin artifact under `public/admin/`.
- [x] `Verified` `public/admin/config.yml` references Git Gateway/Identity-style backend configuration.
- [ ] `Needs review` Confirm whether `/admin` should remain publicly reachable.
- [ ] `Needs review` Identify all admin, deployment, CMS, email, DNS, and hosting accounts.
- [ ] `Needs review` Require strong unique passwords and MFA wherever supported.
- [ ] `Needs review` Limit admin access to required users only.
- [ ] `Needs review` Review recovery email and account recovery settings.
- [x] `Not applicable` The public case-study repository has no runtime authentication surface.

## Privacy Considerations

- [x] `Verified` Public case-study repository contains no contact submissions, analytics data, or personal user data.
- [x] `Verified` Private project contains a privacy-related page: `pages/confidentialitate-aplicatie.tsx`.
- [x] `Verified` Public privacy page returns 200 and mentions contact, email, newsletter, personal data, form, and storage-related terms.
- [ ] `Needs review` Identify all personal data collected through contact forms, newsletter forms, email, analytics, and logs.
- [ ] `Needs review` Minimize collected data and avoid storing unnecessary contact submissions.
- [ ] `Needs review` Document how submissions are handled and retained.
- [ ] `Needs review` Review analytics, logging, and third-party services for privacy impact.
- [ ] `Planned` Confirm privacy policy coverage for current data collection.

## Backup and Recovery

- [x] `Verified` Private project contains mobile backup-related code paths.
- [ ] `Needs review` Identify production backup requirements for content, configuration, deployment settings, DNS records, and documentation.
- [ ] `Needs review` Confirm backups are stored separately from the main project workspace.
- [ ] `Needs review` Test recovery steps periodically.
- [ ] `Needs review` Keep a record of domain, hosting, and email recovery procedures.
- [ ] `Planned` Define recovery time expectations for the project.

## DNS and Email Security

- [x] `Verified` Domain has MX records pointing to Zoho mail infrastructure.
- [x] `Verified` Domain has an SPF TXT record.
- [ ] `Needs review` `_dmarc.tawhid.ro` returned multiple DMARC TXT records; DNS should be cleaned to one effective policy record.
- [ ] `Needs review` Confirm DKIM selectors for active mail providers and document them without exposing secrets.
- [ ] `Needs review` Protect domain registrar account with MFA.
- [ ] `Needs review` Review DNS records for unnecessary exposure.
- [ ] `Needs review` Monitor domain renewal status.
- [ ] `Planned` Document current DNS/email provider setup without exposing sensitive values.

## Deployment Security

- [x] `Verified` Public case-study GitHub repository is public and uses `main` as default branch.
- [x] `Verified` Public response headers identify the production deployment provider as Vercel.
- [x] `Verified` Local Vercel project metadata is present with project and organization identifiers.
- [x] `Verified` Public site apex HTTPS redirects to canonical `https://www.tawhid.ro`.
- [x] `Verified` HTTP requests redirect to HTTPS before canonical routing.
- [x] `Verified` Private project includes redirect/security-header configuration in `next.config.js`.
- [ ] `Needs review` Confirm production access controls in the Vercel dashboard or authenticated CLI.
- [ ] `Needs review` Restrict deployment access to trusted accounts.
- [ ] `Needs review` Use separate production secrets from local development secrets.
- [ ] `Needs review` Review build logs for accidental secret exposure.
- [ ] `Needs review` Review preview deployment exposure if previews are enabled.
