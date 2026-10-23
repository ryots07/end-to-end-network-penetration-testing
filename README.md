# End-to-End Network Penetration Testing Engagement

A lab-based penetration-testing project documenting the path from service discovery to vulnerability research, controlled exploitation, verification of access, traffic observation and remediation recommendations.

**Project type:** Cybersecurity practical / major project  
**Target:** Deliberately vulnerable Metasploitable 2 virtual machine in an authorised lab  
**Tools:** Kali Linux, Nmap, Metasploit Framework, Wireshark

## Quick links

- **[Open the full project report](https://ryots07.github.io/end-to-end-network-penetration-testing/)**
- **[View all cybersecurity projects](https://ryots07.github.io/Portfolio/)**
- **[View this repository](https://github.com/ryots07/end-to-end-network-penetration-testing)**

## Objective

Practise a structured penetration-testing workflow in a controlled environment: identify reachable services, investigate a potential vulnerability, validate the finding safely against the intentionally vulnerable target, record evidence, and suggest defensive improvements.

## What I did

1. **Reconnaissance:** Used Nmap to scan the lab target and identify open ports and service information.
2. **Service investigation:** Identified an FTP service reporting as vsftpd 2.3.4 on port 21 and researched the associated known vulnerability, CVE-2011-2523.
3. **Controlled validation:** Used the relevant Metasploit module against the deliberately vulnerable Metasploitable 2 machine in the authorised lab.
4. **Access verification:** Recorded the successful Meterpreter session and used `getuid` to verify the identity reported by the session.
5. **System and network observations:** Recorded relevant host details and reviewed network information available from the lab session.
6. **Traffic inspection:** Used Wireshark to examine traffic associated with the established session and documented the evidence in the report.
7. **Reporting:** Organised screenshots, methods, findings, impact and remediation suggestions.

## Key findings

- Nmap identified multiple exposed TCP services on the lab target. An open port alone does not prove a vulnerability.
- The FTP service was investigated because its reported version matched a known vulnerability candidate.
- The selected exploit succeeded in the lab and opened a Meterpreter session; the session's `getuid` output reported root-level access.
- The Wireshark capture was taken **after the session had been established**. The filtered view showed session-related TCP packets between Kali's port 4444 and the target's port 56350. It should not be interpreted as a packet-level capture of the initial exploit sequence.

## Defensive recommendations

- Patch or replace vulnerable services and verify software integrity.
- Disable unnecessary services and restrict exposed ports with firewall rules.
- Limit service privileges and isolate network-facing services where practical.
- Prefer secure, authenticated file-transfer options over legacy FTP.
- Monitor system logs, unexpected listeners and network connections.
- Retest after remediation and assess other exposed services individually.

## What this project demonstrates

- Network reconnaissance and service enumeration with Nmap
- Vulnerability research and controlled validation with Metasploit
- Basic session and host information verification
- Traffic inspection with Wireshark
- Evidence collection, technical reporting and remediation thinking

## Scope and responsible use

All testing described here was performed against a deliberately vulnerable virtual machine in an authorised lab environment. These results demonstrate the tested path on that lab target; they are not a claim of access to any real organisation's systems.

---

*Created by Samyak Gautam as part of practical cybersecurity learning.*
