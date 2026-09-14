# Linux Basics

## Purpose

This document records fundamental Linux commands used during cybersecurity training.

## System Identification

### `whoami`

Displays the currently logged-in user.

```bash
whoami
```

### `id`

Displays the user's UID, GID, and group membership.

```bash
id
```

### `pwd`

Displays the current working directory.

```bash
pwd
```

### `ls -la`

Displays files and directories, including hidden files and permission information.

```bash
ls -la
```

## Why These Commands Matter

Understanding the current user, group membership, working directory, and file permissions is important when investigating Linux security issues.

## Security Relevance

Linux security investigations often begin by determining:

1. Which user is active?
2. What privileges does the user have?
3. Which files are accessible?
4. What processes and services are running?
5. What authentication activity has occurred?

These basic commands provide the foundation for more advanced Linux security investigations.
