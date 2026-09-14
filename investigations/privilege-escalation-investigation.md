# Linux Privilege Escalation Investigation

## Overview

This project presents a simulated Linux privilege-escalation investigation designed to demonstrate basic SOC and blue-team analysis skills.

The scenario focuses on identifying suspicious activity in which a standard Linux user attempts to obtain elevated privileges.

> **Training Notice:** This is an educational and simulated investigation. The events and evidence presented here are not from a real production system or security incident.

---

## Investigation Objective

The objectives of this investigation are to:

* Identify suspicious privilege-escalation activity.
* Analyze authentication and system events.
* Determine whether elevated privileges were successfully obtained.
* Identify potential security risks.
* Recommend defensive controls.
* Document the investigation using a SOC-style workflow.

---

## Simulated Scenario

A Linux server contains a normal user account named:

```text
student
```

Security monitoring identifies suspicious activity involving the account.

The following sequence of events is observed:

1. The user logs into the Linux system.
2. The user attempts to execute commands requiring elevated privileges.
3. Multiple authentication attempts occur.
4. A successful privilege escalation is recorded.
5. Administrative commands are executed shortly afterward.

This behavior requires investigation because unauthorized privilege escalation could allow an attacker to modify system configurations, access sensitive files, disable security controls, or establish persistence.

---

## Simulated Evidence

| Time     | User    | Event                           | Result     |
| -------- | ------- | ------------------------------- | ---------- |
| 10:14:02 | student | SSH login                       | Successful |
| 10:16:31 | student | `sudo` authentication attempt   | Failed     |
| 10:16:48 | student | `sudo` authentication attempt   | Failed     |
| 10:17:05 | student | `sudo` authentication attempt   | Successful |
| 10:17:12 | root    | Administrative command executed | Successful |
| 10:18:01 | root    | System configuration accessed   | Successful |

---

## Initial Analysis

The investigation begins with the successful SSH login.

The account `student` initially operates with normal user privileges. Shortly afterward, multiple failed `sudo` authentication attempts are observed.

The subsequent successful authentication is significant because the account transitions from normal-user activity to administrative activity.

The timeline therefore requires additional investigation.

---

## Suspicious Indicators

The following behaviors are considered suspicious:

### 1. Multiple Failed Privilege Attempts

Several failed `sudo` authentication attempts occur within a short period.

Potential explanations include:

* Incorrect password entry.
* Unauthorized use of another user's credentials.
* Password guessing.
* An attacker attempting to obtain administrative privileges.

### 2. Successful Privilege Escalation

A successful `sudo` authentication occurs immediately after the failed attempts.

This is important because successful privilege escalation can provide access to sensitive system resources.

### 3. Administrative Activity

Commands are executed as `root` shortly after successful privilege escalation.

This creates a strong reason to review:

* Commands executed.
* Files accessed.
* System configuration changes.
* New users or groups.
* Scheduled tasks.
* Network connections.
* Security-control modifications.

---

## Investigation Questions

A SOC analyst should investigate:

1. Was the `student` account authorized to use `sudo`?
2. Why were multiple authentication attempts unsuccessful?
3. What command was executed after privilege escalation?
4. Which files were accessed or modified?
5. Were new accounts created?
6. Were user permissions changed?
7. Were security logs modified or deleted?
8. Were suspicious network connections established?
9. Did the activity continue after privilege escalation?
10. Was persistence established?

---

## Risk Assessment

### Risk Level: HIGH

Privilege escalation can significantly increase the impact of a security compromise.

If an unauthorized user obtains root privileges, they may potentially:

* Access protected files.
* Modify system configurations.
* Create new privileged accounts.
* Disable security controls.
* Install malicious software.
* Modify logs.
* Establish persistence.
* Access credentials or sensitive information.

The actual risk depends on whether the activity was authorized and what actions occurred after privilege escalation.

---

## Defensive Recommendations

### 1. Apply Least Privilege

Users should receive only the permissions required for their job responsibilities.

### 2. Review Sudo Configuration

Administrators should regularly review:

```text
/etc/sudoers
```

and related sudo configuration files.

### 3. Monitor Authentication Events

Monitor:

* Successful authentication.
* Failed authentication.
* `sudo` activity.
* Account changes.
* Group membership changes.

### 4. Centralize Logging

Forward important Linux security logs to a centralized logging or SIEM platform.

This helps analysts identify suspicious authentication patterns across multiple systems.

### 5. Protect Administrative Accounts

Administrative access should use strong authentication controls and should be restricted to authorized personnel.

### 6. Monitor Privileged Commands

Privileged command execution should be logged and reviewed when appropriate.

### 7. Investigate Anomalous Behavior

A normal user suddenly performing administrative operations should generate an investigation or alert when inconsistent with expected behavior.

---

## SOC Investigation Workflow

The investigation follows a basic SOC workflow:

```text
Alert
  ↓
Collect Evidence
  ↓
Build Timeline
  ↓
Identify Suspicious Activity
  ↓
Determine Scope
  ↓
Assess Risk
  ↓
Contain
  ↓
Remediate
  ↓
Document Findings
```

---

## MITRE ATT&CK Mapping

This simulated investigation can conceptually relate to:

**T1068 — Exploitation for Privilege Escalation**

The technique describes situations in which an adversary exploits a vulnerability or weakness to obtain higher privileges.

Other techniques may become relevant depending on the evidence discovered during the investigation.

> MITRE ATT&CK mapping is included for educational analysis and does not establish that a real attack occurred.

---

## Example Analyst Conclusion

The investigation identified a suspicious sequence involving multiple failed privilege-authentication attempts followed by successful administrative access.

The activity should be considered potentially suspicious until authorization is confirmed.

Additional investigation should determine:

* Whether the account was authorized to use `sudo`.
* Which commands were executed.
* Whether system files were modified.
* Whether persistence was established.
* Whether additional systems or accounts were affected.

If unauthorized activity is confirmed, the affected credentials should be secured and the system should be investigated for additional compromise.

---

## Skills Demonstrated

This investigation demonstrates knowledge of:

* Linux security
* Authentication analysis
* Privilege management
* Least privilege
* Log analysis
* SOC investigation methodology
* Incident triage
* Risk assessment
* Security hardening
* MITRE ATT&CK concepts
* Security documentation

---

## Learning Outcome

This exercise demonstrates how a cybersecurity analyst can move beyond individual Linux commands and use security evidence to construct a timeline, identify suspicious behavior, assess risk, and recommend defensive controls.
