# IAM Security Investigation Lab

## Case ID
IAM-001

## Investigation Summary
Investigated a failed authentication attempt
followed by successful privileged command execution
on a Kali Linux virtual machine.

## Environment
Operating System: Kali Linux
Hostname: kali-attacker
Account: kali
Log Source: systemd journal
Authentication: Linux PAM and sudo

## Evidence Timeline

19:40:28 - Failed sudo authentication for kali.

19:40:47 - Successful privileged execution
of /usr/bin/whoami.

## Investigation Findings

The account experienced an authentication failure
followed by successful privileged command execution.

The failed authentication was intentionally
generated as part of an authorized lab exercise.

No evidence of unauthorized access was identified.

## Risk Assessment
Severity: Informational
Classification: Authorized testing

## Recommended Response
No account containment required.

Continue monitoring authentication activity.

Escalate if unexpected failures, unfamiliar sources,
or unauthorized privileged activity are observed.

## Conclusion
This investigation demonstrated Linux authentication
log analysis, event correlation, evidence collection,
and security incident documentation.
