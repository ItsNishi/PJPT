# AD Pentest Case Studies

Real-world pentest stories from Heath Adams (TCM Security) that demonstrate AD attack methodology in practice.

---

## Pentest Tales #001: You Spent How Much on Security?

[Full article](https://tcm-sec.com/pentest-tales-001-you-spent-how-much-on-security)

### Scenario

- Client had invested heavily in security products (firewalls, endpoint protection, SIEM, etc.)
- Believed their network was well-defended due to the money spent
- Hired TCM for an internal network pentest

### Attack Path

1. **LLMNR Poisoning** -- Ran Responder on the network, captured NTLMv2 hashes within minutes
2. **Hash Cracking** -- Cracked the captured hashes with Hashcat; passwords were weak despite password policies
3. **Credential Reuse** -- Used the cracked credentials to access SMB shares and found sensitive data
4. **Lateral Movement** -- Sprayed credentials across the network, found admin access on multiple machines
5. **Domain Compromise** -- Escalated to Domain Admin through credential reuse and lateral movement

### Key Takeaways

- **Expensive security products don't fix fundamentals** -- LLMNR was still enabled, passwords were weak, no network segmentation
- **Disable LLMNR and NBT-NS** -- this is low-hanging fruit that attackers will always go for first
- **Enforce strong, unique passwords** -- password policies mean nothing if users pick predictable patterns
- **Security is about configuration, not products** -- the money spent was wasted because nothing was properly configured
- **Internal network assessments matter** -- perimeter defenses don't help when the attacker is already inside

---

## Pentest Tales #002: Digging Deep

[Full article](https://tcm-sec.com/pentest-tales-002-digging-deep)

### Scenario

- More hardened environment than Tale #001
- Common quick wins (LLMNR, weak passwords) were not immediately available
- Required persistence and deeper enumeration to find attack paths

### Attack Path

1. **Initial Enumeration** -- Standard scans and poisoning didn't produce quick results
2. **Thorough Enumeration** -- Went deeper with service enumeration, share hunting, and user discovery
3. **Finding a Foothold** -- Discovered a misconfigured service / exposed credentials through thorough enumeration
4. **Post-Compromise Enumeration** -- Used BloodHound and PowerView to map out the domain
5. **Privilege Escalation** -- Identified an attack path through AD relationships that weren't obvious at first glance
6. **Domain Compromise** -- Chained multiple findings together to reach Domain Admin

### Key Takeaways

- **Enumeration is everything** -- when quick wins fail, enumerate harder and deeper
- **Don't give up early** -- the difference between a failed pentest and a successful one is persistence
- **BloodHound reveals hidden paths** -- AD relationships create attack paths that aren't visible through manual enumeration alone
- **Defense in depth works (partially)** -- the client made it harder, but a determined attacker will find a way
- **Chain small findings** -- individual low-severity findings can combine into critical attack paths

---

## Lessons for the PJPT Exam

These case studies reinforce the methodology tested on the PJPT:

1. **Start with the basics** -- Responder, nmap, enumeration
2. **Crack what you capture** -- always try to crack hashes before moving on
3. **Enumerate after every win** -- new credentials = new enumeration opportunities
4. **Think laterally** -- one compromised host leads to the next
5. **Document everything** -- your report should tell the story of your attack path, just like these case studies
