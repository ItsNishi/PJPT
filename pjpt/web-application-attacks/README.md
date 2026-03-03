# Web Application Attacks

Common web vulnerabilities based on the OWASP Top 10. Understanding these is essential for both web app and network pentests.

## Key Vulnerabilities

| Vulnerability | Impact |
|--------------|--------|
| SQL Injection | Read/write database, potential RCE |
| Cross-Site Scripting (XSS) | Session hijacking, credential theft |
| Command Injection | Direct OS command execution |
| IDOR | Access other users' data |
| File Inclusion (LFI/RFI) | Read files, potential RCE |
| XXE | Read files, SSRF, DoS |

## Testing Methodology

1. Map the application (pages, forms, parameters, APIs)
2. Identify input points (URL params, form fields, headers, cookies)
3. Test each input for injection vulnerabilities
4. Check authentication and authorization controls
5. Look for sensitive data exposure
6. Test file upload functionality

## Tools

- **Burp Suite** -- Intercept and modify requests
- **sqlmap** -- Automated SQL injection
- **ffuf / gobuster** -- Directory and parameter fuzzing
- **nikto** -- Web server scanner
- **wfuzz** -- Web fuzzer for parameters and paths
