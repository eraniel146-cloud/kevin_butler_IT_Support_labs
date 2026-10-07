Linux Password Aging: /etc/login.defs vs. chage
Objective

Understand the difference between system-wide password-aging defaults and password-aging settings applied to an individual Linux account.

Environment
Platform: LabEx
Operating environment: Linux
Account: labex
Step 1 — Identify the Current User

Command:

whoami

Result:

labex
Step 2 — Review the Account's Initial Password-Aging Settings

Command:

sudo chage -l labex

Initial results:

Last password change                                    : Sep 25, 2026
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
Step 3 — Review /etc/login.defs

Command:

grep -E '^(PASS_MAX_DAYS|PASS_MIN_DAYS|PASS_WARN_AGE)' /etc/login.defs

Result:

PASS_MAX_DAYS   99999
PASS_MIN_DAYS   0
PASS_WARN_AGE   7

The values found in /etc/login.defs matched the corresponding password-aging values initially displayed for the labex account.

Step 4 — Modify the Individual Account
Set maximum password age to 90 days

Command:

sudo chage -M 90 labex

Verification:

sudo chage -l labex

Result:

Maximum number of days between password change          : 90

The account's password expiration was calculated as:

Dec 24, 2026
Set minimum password age to 1 day

Command:

sudo chage -m 1 labex

Verification showed:

Minimum number of days between password change          : 1
Maximum number of days between password change          : 90
Set password expiration warning to 14 days

Command:

sudo chage -W 14 labex

Final verification:

sudo chage -l labex

Final results:

Last password change                                    : Sep 25, 2026
Password expires                                        : Dec 24, 2026
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 1
Maximum number of days between password change          : 90
Number of days of warning before password expires       : 14
Troubleshooting Observation

I initially entered:

sudo chage -l Labex

The command returned:

chage: user 'Labex' does not exist in /etc/passwd

I corrected the username to lowercase:

sudo chage -l labex

The command successfully displayed the account information.

This demonstrated that Linux usernames are case-sensitive.

What I Learned

The /etc/login.defs file contains system-wide/default account-management settings, including password-aging parameters such as:

PASS_MAX_DAYS
PASS_MIN_DAYS
PASS_WARN_AGE

The chage command can display and modify password-aging information for an individual account.

In this exercise, I first reviewed the existing configuration and then used chage to modify the labex account independently.

The final account settings were:

Maximum password age: 90 days
Minimum password age: 1 day
Warning period: 14 days
Security Relevance

Password-aging configuration is one component of Linux account security. It should be considered alongside authentication controls, MFA where available, account management, access controls, and organizational security policies.

Changes to production systems should only be made with appropriate authorization.

Commands Practiced
whoami

grep -E '^(PASS_MAX_DAYS|PASS_MIN_DAYS|PASS_WARN_AGE)' /etc/login.defs

sudo chage -l labex

sudo chage -M 90 labex

sudo chage -m 1 labex

sudo chage -W 14 labex
Hands-On Result

This LabEx exercise provided practical experience inspecting Linux password-aging configuration, comparing system-wide defaults with an individual account, modifying account-specific password-aging values, and verifying the resulting configuration.