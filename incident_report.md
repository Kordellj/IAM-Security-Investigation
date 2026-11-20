# IAM-001 — Linux Authentication and Privileged Command Investigation

| Case detail | Value |
| --- | --- |
| Activity date | November 19, 2026 |
| Classification | Authorized lab activity |
| Severity | Informational |
| Environment | Kali Linux VM in Oracle VirtualBox |
| Host and account | `kali-attacker` and `kali` |
| Evidence source | systemd journal, including Linux PAM and `sudo` messages |

## Summary

A deliberately incorrect password triggered a `sudo` authentication failure for the local `kali` account. Nineteen seconds later, the same `sudo` process logged `/usr/bin/whoami` with `root` as the target user. Both events occurred during the authorized lab exercise.

## Timeline

Times are shown as recorded by the VM.

| Time | Recorded event |
| --- | --- |
| 19:40:28 | `pam_unix(sudo:auth)` recorded an authentication failure for `kali` on `/dev/pts/0`. |
| 19:40:47 | `sudo` logged `COMMAND=/usr/bin/whoami` with `USER=root` and `TTY=pts/0`. PAM recorded the root session opening and closing at the same timestamp. |

## Analysis

Both timeline entries contain the hostname `kali-attacker` and the process identifier `sudo[12124]`. The account and terminal fields align across the two records. The root session messages provide supporting context for the privileged command. An earlier LightDM authentication failure was recorded by a different service and was outside this `sudo` event sequence.

## Disposition

The events matched the authorized test. No unauthorized access was identified in the evidence reviewed for this case, so account containment was unnecessary. In an operational environment, unexpected authentication failures, unfamiliar sources, or unexplained privileged commands would warrant further investigation and escalation under the applicable procedures.

## Supporting evidence

- [Original authentication log excerpt](evidence/authentication_events.txt)
- [Paired sudo records](screenshots/01-sudo-authentication-correlation.png)
- [Journal validation and session context](screenshots/02-journal-evidence-validation.png)
- [Evidence export](screenshots/03-journal-evidence-export.png)
