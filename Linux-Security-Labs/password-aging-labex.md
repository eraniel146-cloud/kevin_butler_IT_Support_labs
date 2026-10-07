# Linux Password Aging — LabEx Hands-On Lab

## Objective


Practice Linux password-aging and account-management controls using
`/etc/login.defs` and the `chage` command.


The goal was to understand the difference between system-wide password
aging defaults and settings applied to an individual user account.

---

## Training Platform

- Platform: LabEx
- Environment: Linux terminal
- Account tested: `labex`


## 1. Identify the Current User

Command:

```bash
whoami
## RESULT 
Labex
2. Check Existing Password-Aging Settings

Command:

(/) Bash
sudo chage -l labex

Initial settings included:

Minimum password age: 0 days
Maximum password age: 99999 days
Warning period: 7 days
Password expiration: never
3. Inspect /etc/login.defs

Command:

(/) Bash
grep -E '^(PASS_MAX_DAYS|PASS_MIN_DAYS|PASS_WARN_AGE)' /etc/login.defs

Observed configuration:

PASS_MAX_DAYS   99999
PASS_MIN_DAYS   0
PASS_WARN_AGE   7

These values represent password-aging defaults configured at the
system level.

4. Modify the Individual Account

I used the chage command to modify the password-aging settings for
the labex account.

Maximum password age
sudo chage -M 90 labex

This sets the maximum password age to 90 days.

Minimum password age
sudo chage -m 1 labex

This requires at least 1 day between password changes.

Password expiration warning
sudo chage -W 14 labex

This provides a 14-day warning before password expiration.

5. Verify the Changes

Command:

(/) Bash
sudo chage -l labex

Final settings:

Minimum number of days between password change : 1
Maximum number of days between password change : 90
Number of days of warning before password expires : 14

The account configuration was successfully modified and verified.

Troubleshooting Observation

The command:

(/) Bash
sudo chage -l Labex

returned an error indicating that the user did not exist.

The correct username was:

labex

Linux usernames are case-sensitive, so Labex and labex are treated
as different usernames.

What I Learned

This exercise demonstrated the difference between:

/etc/login.defs

Provides system-level configuration defaults related to account and
password management.

Examples include:

PASS_MAX_DAYS
PASS_MIN_DAYS
PASS_WARN_AGE
chage

Allows password-aging settings to be viewed and modified for an
individual user account.

Important commands practiced:

(/) Bash
sudo chage -l labex
sudo chage -M 90 labex
sudo chage -m 1 labex
sudo chage -W 14 labex
Security Relevance

Password aging is one part of account security and access control.

In a real organization, password-aging settings should be established
according to organizational security policy and applicable requirements.

Password aging should not be considered a replacement for stronger
controls such as:

Multi-factor authentication (MFA)
Strong authentication
Account lockout or risk-based controls
Least privilege
Monitoring and logging
Appropriate identity and access management
Hands-On Skills Demonstrated
Linux command-line navigation
User/account identification
Password-aging management
chage command
/etc/login.defs inspection
Linux configuration inspection
Verification of security settings
Basic troubleshooting
Understanding of account security controls
Evidence

Screenshots documenting the initial and final configurations are stored
in the repository's Evidence directory.

Evidence files:

linux-password-aging-initial.png
linux-password-aging-final.png
Portfolio Note

This lab was completed as hands-on practice using the LabEx Linux
environment. The exercise is part of my ongoing preparation for
CompTIA Security+ and practical Linux/security administration skills.
