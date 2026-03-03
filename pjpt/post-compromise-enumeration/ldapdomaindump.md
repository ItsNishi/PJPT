# ldapdomaindump

Quick Python tool to dump AD info via LDAP. Produces HTML and JSON reports.

## Usage

```bash
# With password
sudo ldapdomaindump ldaps://DC_IP -u 'DOMAIN\username' -p 'password'

# Output goes to current directory
# Creates HTML, JSON, and grep-friendly files
```

## Output Files

| File | Contents |
|------|----------|
| `domain_users.html` | All domain users with attributes |
| `domain_groups.html` | Groups and memberships |
| `domain_computers.html` | Domain-joined computers |
| `domain_policy.html` | Password policy, lockout settings |
| `domain_trusts.html` | Domain trust relationships |

## What to Look For

- **Users with descriptions** -- Often contain passwords or hints
- **Password policy** -- Lockout threshold, complexity requirements
- **Group memberships** -- Who is in privileged groups
- **Computer OS versions** -- Old/unsupported systems are easy targets
- **Service accounts** -- Often over-privileged and Kerberoastable

**Note:** Quick and easy first step after compromising credentials. Run this before deeper enumeration with PowerView or BloodHound.
