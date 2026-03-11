# Security Policy

## Supported Versions

`msms` is actively maintained on the default branch.
Security fixes are applied to the latest code on `main`.

| Version | Supported |
| --- | --- |
| latest (`main`) | Yes |
| older commits | No |

## Reporting a Vulnerability

Please do **not** report security vulnerabilities in public issues or discussions.

Use one of the following private channels:

1. GitHub Security Advisories: <https://github.com/iptoux/msms/security/advisories>
2. Maintainer email: `iptoux@nobody.com`

If needed, you can also contact the maintainer via X/Twitter as listed in the repository community docs.

## What to Include in a Report

Please include as much detail as possible:

- A clear description of the issue and potential impact
- Affected package/app/path (for example: `apps/admc`, `apps/frontend`, `packages/ui`)
- Reproduction steps
- Proof of concept, logs, or screenshots (if available)
- Suggested mitigation (optional)

## Security Focus Areas

When auditing this repository, prioritize:

- Authentication and authorization checks
- Server/client boundary violations
- Secret and environment variable exposure
- Input validation and sanitization
- Excessive data exposure in API or server responses
- Dependency vulnerabilities across workspace packages

## Response Timeline

- Initial acknowledgement: within 72 hours
- Triage status update: within 7 days
- Fix timeline: based on severity and exploitability

Critical vulnerabilities are prioritized.

## Disclosure Policy

This project follows coordinated disclosure:

1. Issue is privately validated and triaged
2. Fix is prepared and reviewed
3. Advisory is published when appropriate
4. Reporter is credited unless anonymity is requested

Thank you for helping keep `msms` and its users safe.
