# IAM Security Investigation — Linux Authentication Analysis

## Overview
This project documents an authorized security investigation
into a failed Linux authentication attempt followed by
successful privileged command execution.

## Environment
- Kali Linux VM (VirtualBox)
- Linux PAM and sudo
- systemd journal
- Tools: journalctl, grep, nano

## Investigation
A deliberately incorrect sudo password produced an
authentication failure for the kali account.

A subsequent successful sudo operation executed
/usr/bin/whoami.

## Evidence Timeline

| Date and time | Observation |
|---|---|
| Nov 19, 2026, 19:40:28 | Failed sudo authentication |
| Nov 19, 2026, 19:40:47 | Successful privileged command execution |

## Findings
The events were correlated using timestamps, account
identifiers, and sudo log messages.

This was authorized testing, not a confirmed incident.

## Skills Demonstrated
- Authentication log analysis
- PAM and sudo event interpretation
- Privileged access monitoring
- Event correlation
- Evidence preservation
- Incident documentation

## Conclusion
No unauthorized access was identified in the reviewed
evidence.

See incident_report.md for the investigation report.
