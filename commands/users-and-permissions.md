# Linux Users, Groups & File Permissions

## 🎯 Objective

This section introduces Linux user accounts, groups, ownership, and file permissions.

Understanding these concepts is important for cybersecurity because improper permissions can allow unauthorized users to access, modify, or execute sensitive files.

---

## 1. User Identity

### `whoami`

Displays the username of the currently active user.

```bash
whoami
```

### `id`

Displays information about the current user, including:

* User ID (UID)
* Group ID (GID)
* Group membership

```bash
id
```

### Security Relevance

When investigating a Linux system, identifying the current account and its privileges is an important first step.

---

## 2. Linux Groups

Linux uses groups to manage access to resources.

A user can belong to one or more groups.

Example:

```bash
groups
```

This displays the groups associated with the current user.

### Security Relevance

Group membership can determine whether a user can access administrative or sensitive resources.

Excessive group privileges can create security risks.

---

## 3. File Ownership

Linux files normally have:

* An owner
* A group
* Permissions for the owner
* Permissions for the group
* Permissions for everyone else

The command:

```bash
ls -l
```

can be used to inspect file ownership and permissions.

Example:

```text
-rw-r--r-- 1 user user 1024 example.txt
```

---

## 4. Understanding Permissions

Linux permissions are represented using:

```text
r = read
w = write
x = execute
```

They are applied to:

```text
user | group | others
```

For example:

```text
-rwxr-xr--
```

can be interpreted as:

```text
User:   rwx
Group:  r-x
Others: r--
```

---

## 5. Changing Permissions

The `chmod` command can modify file permissions.

Example:

```bash
chmod 600 sensitive.txt
```

This gives the owner read and write permissions while removing permissions from group members and other users.

### Security Relevance

Sensitive files should not unnecessarily be readable or writable by every user on a system.

---

## 6. Least Privilege

A core cybersecurity principle is **least privilege**.

Users and processes should receive only the permissions required to perform their legitimate tasks.

For example, a user who only needs to read a configuration file should not automatically receive permission to modify it.

---

## 🔐 Security Risks

Poor Linux permissions can lead to:

* Unauthorized data access
* Unauthorized modification
* Privilege escalation
* Exposure of credentials
* Modification of system configuration
* Data destruction

---

## 🔎 Investigation Questions

When examining Linux permissions, an analyst should ask:

1. Who owns the file?
2. Which group owns the file?
3. Who can read it?
4. Who can modify it?
5. Who can execute it?
6. Are permissions broader than necessary?
7. Could excessive permissions create a security risk?

---

## 🎯 Key Takeaway

Understanding Linux users, groups, ownership, and permissions provides the foundation for investigating unauthorized access and privilege-related security issues.
