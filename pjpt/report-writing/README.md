# Report Writing

The pentest report is the primary deliverable. A well-written report is what separates a professional engagement from "just hacking."

## Report Sections

### 1. Executive Summary

- Written for non-technical stakeholders (C-suite, managers)
- High-level overview of scope, findings, and risk
- No technical jargon
- Business impact focus
- Overall risk rating

### 2. Scope and Methodology

- What was tested (IP ranges, domains, applications)
- What was NOT tested (exclusions)
- Testing methodology (OWASP, PTES, OSSTMM)
- Timeline of the engagement
- Type of test (black box, grey box, white box)

### 3. Findings Summary

- Table of all findings sorted by severity
- Severity ratings: Critical, High, Medium, Low, Informational
- Use CVSS scores for consistency

### 4. Technical Findings (Detail)

Each finding should include:

| Section | Description |
|---------|-------------|
| Title | Clear, descriptive name |
| Severity | Critical / High / Medium / Low / Info |
| CVSS Score | Standardized risk rating |
| Description | What the vulnerability is |
| Impact | What an attacker could do |
| Affected Systems | IPs, URLs, hosts |
| Evidence | Screenshots, command output, proof |
| Remediation | How to fix it |
| References | CVEs, vendor advisories, OWASP links |

### 5. Remediation Summary

- Prioritized list of fixes
- Quick wins vs long-term improvements
- Strategic recommendations

### 6. Appendices

- Raw tool output (Nmap, Nessus scans)
- Full hash dumps
- Detailed attack chains
- Methodology details

## Severity Ratings

| Rating | Description | Example |
|--------|-------------|---------|
| Critical | Immediate compromise, no auth required | Unauthenticated RCE, SQLi to DA |
| High | Significant impact, some conditions | Authenticated RCE, credential dumps |
| Medium | Moderate impact, requires access | Stored XSS, IDOR to limited data |
| Low | Minor impact | Information disclosure, verbose errors |
| Informational | Best practice, no direct risk | Missing headers, outdated banners |

## Tips

- Screenshots are essential -- prove every finding
- Write findings as you go, not at the end
- Remediation advice should be actionable and specific
- Proofread -- typos and grammar errors undermine credibility
- Include positive findings too ("no SQLi found on login form")
- Tailor language to the audience
