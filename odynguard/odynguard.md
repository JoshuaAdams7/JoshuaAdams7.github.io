---
layout: default
---

# Overview

Odynguard scans local and remote hosts over SSH. It checks them against CIS-aligned controls, tracks missing patches and vulnerabilities, and shows overall security posture on a single dashboard.

## Why Was It Built?

I wanted to test whether or not leveraging AI-based services for the creation of security tooling would be viable.

By extension, manual posture checks are slow and can be inconsistent, and I wanted to see how much of the security assessment process could be automated.

# Key Features

* Posture dashboard, which includes a configurable score with trend and change history.
* CIS benchmark checks, plus patch and vulnerability tracking.
* Agentless multi-host scanning over SSH.
* Audit log of every command run, with timestamps.
* Exceptions and risk acceptance, plus guided remediation.
* Scheduled scans, and report export to PDF, CSV and JSON.

# Architecture

...

# Sample Findings

| Finding        | Severity          | Control | Remediation
|:-------------|:------------------|:------|
| test           | test | test  |
| test | test   | test  |
| test           | test      | test   |
| test           | test | test  |


# Security Considerations

* Scanning is read-only by default. remediation only runs  with explicit approval.
* Authentication is key-based, and no credentials are stored in plain text.
* Every scan produces a full command audit trail.

## Known Limitations

...

# Roadmap

...
