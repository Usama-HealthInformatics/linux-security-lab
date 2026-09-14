# 🔐 SSH Security

## 🎯 Objective

This section introduces Secure Shell (SSH), a protocol commonly used to securely access and administer Linux systems remotely.

The goal is to understand how SSH authentication works, common security risks, and defensive measures used to protect SSH services.

---

## 1. What Is SSH?

**SSH (Secure Shell)** is a network protocol used to securely connect to a remote computer.

A typical connection can be represented as:

```text
Administrator
     │
     │ Encrypted SSH Connection
     ▼
Linux Server
```

SSH provides encrypted communication between the client and server.

---

## 2. Common SSH Uses

SSH can be used for:

* Remote Linux administration
* Secure file transfer
* System maintenance
* Server management
* Security administration
* Remote command execution

---

## 3. SSH Authentication

SSH commonly supports different authentication methods.

### Password Authentication

The user provides a username and password.

```text
User
 │
 ├── Username
 └── Password
       │
       ▼
    SSH Server
```

### Public-Key Authentication

Public-key authentication uses a cryptographic key pair:

```text
Private Key → kept secret by the user

Public Key → stored on the server
```

The private key should never be shared.

---

## 4. SSH Security Risks

Poorly secured SSH services can become targets for:

* Password guessing
* Credential attacks
* Brute-force attempts
* Compromised credentials
* Unauthorized remote access

An exposed SSH service should therefore be properly secured and monitored.

---

## 5. Failed Authentication

Repeated failed SSH authentication attempts can be an indicator of suspicious activity.

A security analyst may investigate:

```text
Failed login
     ↓
Identify account
     ↓
Identify source IP
     ↓
Check timestamp
     ↓
Look for repeated attempts
     ↓
Determine whether activity is suspicious
```

---

## 6. Security Monitoring

SSH authentication events can provide useful evidence during a security investigation.

An analyst may examine:

* Username
* Source IP address
* Timestamp
* Authentication result
* Number of attempts
* Successful login after multiple failures

A sequence such as:

```text
Multiple failed attempts
          ↓
Successful authentication
          ↓
Unusual account activity
```

may require further investigation.

---

## 7. SSH Hardening

Common defensive measures include:

### Strong Authentication

Use strong credentials and, where appropriate, public-key authentication.

### Disable Unnecessary Access

SSH access should only be available to users who require it.

### Least Privilege

Administrative privileges should be limited to authorized accounts.

### Monitoring

Authentication events should be monitored for unusual patterns.

### Updates

Keep the operating system and SSH software updated.

### Network Restrictions

Where appropriate, restrict SSH access to trusted networks or authorized source addresses.

---

## 8. Security Investigation Questions

When investigating suspicious SSH activity, an analyst should ask:

1. Which account was targeted?
2. Where did the connection originate?
3. When did the activity occur?
4. How many authentication attempts occurred?
5. Was authentication eventually successful?
6. Was the account authorized to access the system?
7. What activity occurred after authentication?

---

## 🛡️ Defensive Perspective

The goal of SSH security monitoring is not simply to detect failed passwords.

A security analyst should establish a timeline and determine whether authentication activity represents:

* Normal administrative activity
* Misconfiguration
* A compromised credential
* Automated password guessing
* Potential unauthorized access

---

## ⚠️ Authorized Testing Only

Security testing should only be performed against systems that you own or have explicit permission to test.

This repository focuses on defensive learning and authorized laboratory environments.

---

## 🎯 Key Takeaway

SSH is an essential Linux administration technology and an important source of security telemetry.

Understanding authentication, monitoring failed attempts, investigating suspicious connections, and applying defensive controls are fundamental skills for cybersecurity and SOC roles.
