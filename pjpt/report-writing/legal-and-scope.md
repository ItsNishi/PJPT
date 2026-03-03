# Legal Documents and Scope

Never start testing without proper authorization. Unauthorized testing is illegal regardless of intent.

## Key Documents

### Rules of Engagement (ROE)

Defines what you can and cannot do during the engagement:

- **Testing hours** -- Business hours only? After hours?
- **Testing methods** -- Social engineering allowed? Physical access?
- **Targets** -- Specific IPs, ranges, domains in scope
- **Exclusions** -- Systems to avoid (production databases, critical infra)
- **Communication** -- Who to contact if something breaks
- **Emergency contacts** -- Phone numbers for immediate escalation
- **Data handling** -- How to store and transmit sensitive findings

### Statement of Work (SOW)

Contract defining the engagement:

- Scope of work
- Deliverables (report format, presentation)
- Timeline and milestones
- Cost and payment terms
- Liability and indemnification

### Permission to Test / Authorization Letter

- Written permission from the system owner
- Signed by someone with authority to authorize testing
- Specifies exactly what systems are in scope
- **Keep this on you during the engagement**

### Non-Disclosure Agreement (NDA)

- Protects client's confidential information
- Covers findings, vulnerabilities, and data discovered
- Usually mutual (protects both parties)

## Scope Definition

### In Scope

Be explicit:

```
- 10.10.10.0/24 (internal network)
- app.example.com (web application)
- mail.example.com (mail server)
- Active Directory domain: corp.example.com
```

### Out of Scope

```
- 10.10.10.50 (production database -- do not touch)
- Third-party hosted services
- Physical security testing
- Social engineering against end users
- Denial of Service testing
```

## Important Rules

- **If it's not in scope, don't touch it**
- **Document everything** -- timestamps, commands, screenshots
- **Stop and communicate** if you find evidence of a real breach
- **Never exfiltrate real PII/PHI/PCI data** -- redact in reports
- **Get explicit re-authorization** if scope changes mid-engagement
- Laws vary by jurisdiction -- understand local regulations (CFAA in US, CMA in UK)
