# tawhid.ro Case Study

Public portfolio case-study repository for the private `tawhid.ro` project.

This repository does not contain production source code, private configuration, secrets, deployment credentials, or unpublished content. It exists to document the project in a professional, security-aware way for a cybersecurity/web portfolio.

## Overview

`tawhid.ro` is a Romanian Islamic educational platform focused on making Islamic educational material easier to access, read, and navigate for Romanian-speaking users.

The private project includes a modern web application and supporting content workflow. This public repository documents the project goals, technical direction, AI-assisted workflow, and security considerations without exposing the private implementation.

## Problem

Romanian-speaking audiences can face friction when looking for structured Islamic educational material online. Useful content may be scattered, hard to navigate, inconsistently formatted, or unavailable in a Romanian-focused experience.

The project addresses this by organizing Islamic educational content into a web platform designed for readability, discoverability, and responsible maintenance.

## Solution

The private project builds a Romanian Islamic education platform with:

- Structured article and educational content presentation
- Web-first reading experience
- Search engine and metadata considerations
- Contact and communication surfaces that require spam and privacy review
- Ongoing content workflow and review responsibilities

## Architecture

```mermaid
flowchart LR
    visitor["Visitor"] --> site["Public Next.js site"]
    site --> content["Structured Islamic content"]
    site --> contact["Contact surface"]
    site --> metadata["SEO metadata and public pages"]

    privateRepo["Private source repository"] --> deploy["Deployment platform\nTODO: confirm provider"]
    deploy --> site
    dns["Domain, DNS, and email"] --> site
    security["Security review\nsecrets, headers, XSS, forms, DNS"] --> privateRepo
    security --> deploy
    security --> dns
```

This diagram is intentionally high-level. It does not expose private source code, credentials, infrastructure identifiers, or unpublished implementation details.

## Tech Stack

Verified technologies used in the private project:

- Next.js
- React
- TypeScript
- Tailwind CSS
- Framer Motion
- lucide-react

TODO: Confirm public deployment provider before publishing this case study.

TODO: Confirm whether any additional public-facing services should be listed.

## My Role

I led the project direction and took responsibility for planning, research, content structure, prompting, review, deployment direction, and security direction.

My responsibilities included:

- Defining the educational and technical goals
- Planning the content structure and user-facing experience
- Researching implementation options and project constraints
- Prompting and directing AI-assisted development tools
- Reviewing generated code and project changes
- Running checks and reviewing deployment readiness
- Identifying security and privacy risks that need active management

## AI-Assisted Development

The project was built with AI-assisted development tools. AI helped with implementation support, code generation suggestions, documentation drafting, debugging assistance, and review checklists.

AI did not replace project ownership. I remain responsible for understanding the system, reviewing changes, maintaining the project, validating behavior, and securing the deployment.

See `AI_ASSISTED_WORKFLOW.md` for more detail.

## Security Focus

The project is treated as a public web platform where user trust, content integrity, domain control, and private operational access matter.

Security focus areas include:

- Keeping secrets and environment variables out of source control
- Reviewing dependencies and update risk
- Reducing XSS risk in rendered content
- Protecting contact forms from spam and abuse
- Applying security headers where appropriate
- Protecting deployment, DNS, email, and admin access
- Considering privacy risks for contact form submissions
- Planning backup and recovery procedures

See `SECURITY_REVIEW.md` and `THREAT_MODEL.md` for the working checklist and simple threat model.

## Screenshots

Screenshots captured from the public `tawhid.ro` website.

### Homepage, Desktop

![Homepage desktop screenshot](assets/screenshots/homepage-desktop.png)

### Article Page, Desktop

![Article page desktop screenshot](assets/screenshots/article-desktop.png)

### Articles Index, Desktop

![Articles index desktop screenshot](assets/screenshots/articles-index-desktop.png)

### Homepage, Mobile

![Homepage mobile screenshot](assets/screenshots/homepage-mobile.png)

### Article Page, Mobile

![Article page mobile screenshot](assets/screenshots/article-mobile.png)

These screenshots show public pages only. They do not show private dashboards, unpublished content, analytics, secrets, admin panels, or personal data.

## Future Improvements

- Refresh screenshots when the public website design changes
- Expand screenshot captions with short feature notes
- Document the content review workflow at a high level
- Confirm deployment provider and public infrastructure details before listing them
- Expand the security review after any form, admin, or authentication changes
- Add a maintenance checklist for dependency updates, backups, and DNS/email security
