# 🔎 Linux Security Log Analysis

## 🎯 Objective

System logs provide important evidence during cybersecurity investigations.

This section introduces Linux authentication logs and explains how security analysts can use log data to identify unusual authentication activity.

---

## 1. What Are System Logs?

Linux systems generate logs that record system and application activity.

Logs can contain information about:

* User authentication
* Login attempts
* System services
* Administrative actions
* Errors
* Network activity
* Security events

For cybersecurity analysts, logs are an important source of evidence.

---

## 2. Authentication Logs

Authentication logs can record events related to users accessing a Linux system.

Depending on the Linux distribution, authentication information may be stored in files such as:

```text
/var/log/auth.log
```

or:

```text
/var/log/secure
```

The exact location depends on the operating system and configuration.

---

## 3. Important Authentication Events

Security analysts may encounter events such as:

### Successful Authentication

A legitimate user successfully authenticates to the system.

```text
Successful login
       ↓
Identify user
       ↓
Identify source
       ↓
Verify activity is expected
```

### Failed Authentication

An authentication attempt fails.

```text
Failed login
       ↓
Identify account
       ↓
Identify source IP
       ↓
Check frequency
       ↓
Determine whether activity is suspicious
```

---

## 4. Important Log Fields

When reviewing an authentication event, an analyst should identify:

| Field                 | Purpose                                          |
| --------------------- | ------------------------------------------------ |
| Timestamp             | Determines when the event occurred               |
| Username              | Identifies the targeted or authenticated account |
| Source IP             | Identifies the originating network address       |
| Authentication result | Determines success or failure                    |
| Service               | Identifies the service involved                  |
| Event sequence        | Helps establish a timeline                       |

---

## 5. Detecting Suspicious Patterns

One failed login does not necessarily indicate an attack.

Analysts should look for patterns.

For example:

```text
09:10  Failed login
09:11  Failed login
09:11  Failed login
09:12  Failed login
09:12  Failed login
09:13  Successful login
```

This sequence may require investigation.

The analyst should determine:

* Was the user expected to log in?
* Was the source IP authorized?
* Was the successful login associated with the same account?
* What happened after authentication?
* Were privileged actions performed?

---

## 6. Timeline Analysis

A timeline helps analysts understand the sequence of events.

Example:

```text
Authentication Failure
        ↓
Repeated Attempts
        ↓
Successful Authentication
        ↓
Account Activity
        ↓
Investigation
```

Establishing a timeline can help distinguish normal activity from potentially malicious behavior.

---

## 7. Security Investigation Workflow

A basic authentication investigation can follow this process:

```text
Collect Logs
     ↓
Identify Authentication Events
     ↓
Filter Failed Attempts
     ↓
Group Events by Account/IP
     ↓
Check for Repeated Attempts
     ↓
Look for Successful Authentication
     ↓
Build Timeline
     ↓
Assess Risk
     ↓
Recommend Mitigation
```

---

## 8. Questions for a SOC Analyst

When reviewing authentication logs, ask:

### Who?

Which account was involved?

### When?

When did the activity occur?

### Where?

What source IP or system generated the activity?

### What?

Was authentication successful or unsuccessful?

### How often?

Was this a single event or a repeated pattern?

### What happened next?

Did additional suspicious activity occur after authentication?

---

## 9. Possible Indicators of Suspicious Activity

Examples include:

* Numerous failed authentication attempts
* Authentication from an unexpected source
* Login activity at unusual times
* Successful authentication after many failures
* Attempts against multiple accounts
* Privileged account activity that is unexpected

These indicators do not automatically prove malicious activity. They should be investigated in context.

---

## 10. Defensive Responses

Depending on the investigation, defensive measures may include:

* Resetting compromised credentials
* Disabling unauthorized accounts
* Restricting SSH access
* Implementing stronger authentication
* Reviewing account privileges
* Blocking malicious sources where appropriate
* Increasing monitoring
* Investigating additional system activity

---

## 🧠 SOC Perspective

Log analysis is one of the fundamental skills used by Security Operations Center (SOC) analysts.

A SOC analyst does not simply look for individual events.

The analyst connects multiple events to determine:

```text
What happened?
       ↓
When did it happen?
       ↓
Who was involved?
       ↓
Where did it originate?
       ↓
Was it authorized?
       ↓
What should happen next?
```

---

## ⚠️ Important Note

The examples in this document are educational scenarios.

Actual security investigations should only be performed on systems that you own or have explicit authorization to monitor.

---

## 🎯 Key Takeaway

Linux authentication logs provide valuable security evidence.

Learning to identify authentication events, recognize suspicious patterns, build timelines, and recommend defensive actions provides a foundation for SOC and incident-response work.
