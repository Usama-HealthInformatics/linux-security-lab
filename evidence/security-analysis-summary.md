# Linux Security Analysis Summary

## Project Overview

This repository documents a structured Linux security learning project focused on system administration, authentication security, permissions, log analysis, privilege management, and security hardening.

The project is designed from a defensive cybersecurity and SOC perspective.

---

## Security Areas Covered

### Linux Command-Line Fundamentals

Documented essential Linux commands and their security relevance, including:

* User identification
* User and group information
* Current working directory
* Directory and file inspection
* Hidden-file identification

### Users and Permissions

Covered:

* Linux users and groups
* File ownership
* Read/write/execute permissions
* `chmod`
* Least-privilege principles
* Risks associated with excessive permissions

### SSH Security

Covered:

* SSH authentication
* Authentication risks
* Failed login monitoring
* SSH hardening
* Administrative access controls

### Linux Log Analysis

Covered:

* Authentication logs
* Successful login events
* Failed authentication attempts
* Log fields
* Suspicious authentication patterns
* Timeline-based investigation

---

## Security Investigations

### SSH Authentication Investigation

A simulated authentication investigation was developed to analyze a sequence of failed SSH authentication attempts followed by a successful login.

The investigation demonstrates:

* Evidence collection
* Timeline construction
* Suspicious activity identification
* Risk assessment
* Defensive recommendations
* MITRE ATT&CK conceptual mapping

### Privilege Escalation Investigation

A simulated investigation was developed around suspicious `sudo` activity and potential unauthorized privilege escalation.

The investigation examines:

* Failed privilege-authentication attempts
* Successful administrative access
* Root-level activity
* Investigation questions
* Risk assessment
* Defensive controls

> These investigations are educational simulations and should not be interpreted as real-world incident experience.

---

## Security Hardening

The project documents defensive controls including:

* Least privilege
* Secure authentication
* SSH hardening
* Account management
* File permissions
* System updates
* Security logging
* Network exposure reduction
* Backup and recovery

---

## SOC Perspective

A security analyst investigating Linux activity should consider the following workflow:

```text
Alert
  ↓
Collect Evidence
  ↓
Analyze Logs
  ↓
Build Timeline
  ↓
Identify Suspicious Behavior
  ↓
Assess Risk
  ↓
Contain
  ↓
Remediate
  ↓
Document Findings
```

The project demonstrates how basic Linux knowledge can support security monitoring and incident investigation.

---

## Skills Demonstrated

* Linux Security
* Linux Command Line
* Authentication Analysis
* SSH Security
* File Permissions
* User and Group Management
* Log Analysis
* Privilege Management
* Incident Triage
* Security Hardening
* SOC Investigation
* MITRE ATT&CK Concepts
* Technical Documentation

---

## Career Relevance

This project supports development toward entry-level roles such as:

* SOC Analyst
* Cybersecurity Analyst
* Junior Security Analyst
* Security Operations Intern
* Linux Security Analyst
* Cloud Security Trainee

The project is part of a broader cybersecurity portfolio focused on Linux, networking, SOC operations, cloud security, and security automation.
