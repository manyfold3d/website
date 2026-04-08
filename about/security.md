---
title: Security
parent: About
layout: page
nav_order: 4
---

We make every effort to ensure Manyfold is a secure platform. This page explains how we test that, and deal with vulnerabilities. The [security section of the admin guide](/sysadmin/security) explains how to configure security-related settings for public servers.

## Penetration Testing

As part of our funding from [NGI Zero](https://ngi-0.eu), we have had two professional penetration tests carried out by [Radically Open Security](https://www.radicallyopensecurity.com). You can download the full reports here:

* [June 2024](/downloads/NGIE%20Manyfold%20penetration%20test%20report%202024.pdf)
* [December 2025](/downloads/NGICore%20Manyfold%20penetration%20test%20report%202025.pdf)

Note that almost all the issues raised in these reports were immediately fixed, with the exception of a couple of low-impact issues which are design improvements rather then vulnerabilities.

Our next audit is planned to take place in Q4 2026.

## Open Bugs & Future Improvements

Issues with security implications are tagged as such on GitHub:

* [Open bugs](https://github.com/manyfold3d/manyfold/issues?q=is%3Aissue%20state%3Aopen%20label%3Abug%20label%3Asecurity)
* [Future improvements & features](https://github.com/manyfold3d/manyfold/issues?q=is%3Aissue%20state%3Aopen%20-label%3Abug%20label%3Asecurity)

## Vulnerability reporting and CVEs

We use GitHub's vulnerability reporting system for security issues. If you find a security vulnerability in Manyfold, please fill in the [vulnerability reporting form](https://github.com/manyfold3d/manyfold/security/advisories/new), or email [security@manyfold.app](mailto:security@manyfold.app)
to let us know confidentially.

We publicise and credit all security advisories and issues when safe to do so. Our full [list of advisories](https://github.com/manyfold3d/manyfold/security/advisories) can be found on GitHub.

## Updates & Dependencies

At least until we reach v1.0, only the latest release version is supported with security updates. Track `latest` and check for updates regularly.

We automatically apply dependency updates (minor and patch versions) as they become available through GitHub's dependabot system, and releases will always incorporate the latest updates.

## Cyber Resiliency Act (CRA)

As a small non-commercial open source project, we don't provide a blanket CRA Declaration of Conformity, and as far as we understand it, we don't actually need to (see OpenSSF's [CRA guide for open source maintainers](https://best.openssf.org/CRA-Brief-Guide-for-OSS-Developers) for more explanation).

If you want to provide a commercial service that uses Manyfold, please get in touch with [services@manyfold.app](mailto:services@manyfold.app) to explore potential commercial support options.
