# Security policy

## Reporting a vulnerability

Please report security issues privately, not in a public issue.

- **On GitHub:** [report a vulnerability](https://github.com/jsonherodev/jsonhero.dev/security/advisories/new). Only you and the maintainer can see the report.
- **By email:** [hello@jsonhero.dev](mailto:hello@jsonhero.dev?subject=Security), with "Security" in the subject.

Tell me what you found, how to reproduce it, and what an attacker could do with it. jsonhero.dev is run by one person, so I'll reply as soon as I can, usually within a few days, and keep you updated until it's fixed.

Please test with your own account and your own share links. If you reach someone else's shared JSON, stop there, don't keep a copy, and include only the link id in your report.

## In scope

- The jsonhero.dev web app: the editor, share links (`jsonhero.dev/s/…`), sign-in, and the billing page
- Anything that lets someone read, change or delete another person's shared JSON or account
- Anything that sends editor contents off the device when the user hasn't clicked Share
- Share link ids that are predictable, and ways around the rate limits

## Out of scope

- Share links being viewable by anyone who has the link, and analytics recording a share link's address and title. Both are by design and documented in [PRIVACY.md](PRIVACY.md).
- Denial-of-service or volumetric attacks, and brute-force guessing of share link ids
- Reports from automated scanners with no demonstrated impact
- Social engineering and phishing
- Vulnerabilities in Paddle's checkout, which should be reported to Paddle directly

Hardening suggestions without an exploit, such as missing headers, are welcome as a regular issue.
