---
layout: default
---

# Overview

Odynguard scans local and remote hosts over SSH. It checks them against CIS-aligned controls, tracks missing patches and vulnerabilities, and shows overall security posture on a single dashboard.

## Why Was It Built?

...

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

...


# Security Considerations

* Scanning is read-only by default. remediation only runs  with explicit approval.
* Authentication is key-based, and no credentials are stored in plain text.
* Every scan produces a full command audit trail.

## Known Limitations

...

# Roadmap

...
