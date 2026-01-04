# Security Policy

## 🔒 Supported Versions

This project is actively maintained on the `main` branch.
Only the latest version is supported with security updates.

| Version | Supported |
|--------|-----------|
| main   | ✅ Yes    |
| older | ❌ No     |

---

## 🚨 Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly.

### How to report:
- Open a **private GitHub security advisory**, or
- Contact the repository owner directly via GitHub

Please **do not** open a public issue for security-related concerns.

---

## 🛡️ Security Considerations

This repository:
- Uses GitHub-hosted runners only
- Does not process user input
- Does not store secrets other than GitHub-provided tokens
- Uses Docker images from trusted public registries
- Uses the default `GITHUB_TOKEN` with minimal required permissions

All workflows are designed to minimize attack surface and follow
GitHub Actions security best practices.

---

## 🔐 Dependency Updates

Docker images and GitHub Actions used in this repository
should be kept up to date to ensure security patches are applied.

---

## 📄 Disclosure Policy

Verified vulnerabilities will be addressed as soon as reasonably possible.
Credit will be given to reporters when appropriate.

---

Thank you for helping keep this project secure.
