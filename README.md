# SOC Lab 05 — Linux Log Analysis & Security Monitoring

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Lab Objectives](#lab-objectives)
3. [Environment Overview](#environment-overview)
4. [Log Investigation Workflow](#log-investigation-workflow)
5. [Log Analysis](#log-analysis)
6. [Detection Engineering Insights](#detection-engineering-insights)
7. [Evidence](#evidence)
8. [Conclusions](#conclusions)
9. [Next Steps](#next-steps)

---

## Executive Summary
This lab focuses on analyzing Linux authentication and system logs to detect suspicious activity.  
System logs provide critical visibility into user activity, authentication attempts, and privilege escalation events.

By investigating authentication logs, security analysts can identify brute-force attacks, unauthorized access attempts, and suspicious administrative activity.

This lab demonstrates how SOC analysts use Linux log data to monitor systems and detect potential security incidents.

---

## Lab Objectives

- Investigate Linux authentication logs
- Identify successful and failed login attempts
- Detect suspicious authentication activity
- Analyze privilege escalation using `sudo`
- Understand how log monitoring supports SOC detection workflows

---

## Environment Overview

**Operating System:** Ubuntu Linux (Virtual Machine)

**Logs Analyzed**
- `/var/log/auth.log`

**Tools Used**
- `grep`
- `cat`
- `less`
- Linux terminal

---

## Log Investigation Workflow
### 1. View Authentication Logs

Authentication logs record login attempts, SSH access, and privilege escalation activity.  
Security analysts regularly review these logs to identify suspicious authentication behavior.

**Command:**

```bash
sudo cat /var/log/auth.log
```

**Explanation**

- `sudo` allows access to protected system logs
- `cat` prints the contents of the log file
- `/var/log/auth.log` contains authentication events such as SSH login attempts and sudo activity

This command allows analysts to review raw authentication activity on the system.

### 2. Detect Failed Login Attempts

Failed authentication attempts can indicate brute-force attacks or unauthorized login activity.  
Security analysts search authentication logs to identify repeated login failures and suspicious access attempts.

**Command:**

```bash
grep "Failed password" /var/log/auth.log
```

**Explanation**

- `grep` searches text within log files
- `"Failed password"` identifies unsuccessful SSH login attempts
- `/var/log/auth.log` contains authentication-related events

This command helps analysts quickly identify failed login attempts that may indicate malicious activity.

### 3. Identify Successful Logins

Successful authentication events are recorded when a user logs into the system using valid credentials.  
Security analysts review these entries to confirm legitimate access and detect unusual login activity.

**Command:**

```bash
grep "Accepted password" /var/log/auth.log
```

**Explanation**

- `grep` searches text within log files
- `"Accepted password"` identifies successful SSH login events
- `/var/log/auth.log` records authentication activity on the system

This command allows analysts to verify successful login events and correlate them with other security activity.
