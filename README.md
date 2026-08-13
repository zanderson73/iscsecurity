# ISCSECURITY Master Class Series

Official static site and curriculum repository for [iscsecurity.org](https://iscsecurity.org).

Authorization-first ethical hacking training focused on real enterprise tradecraft, defensive visibility, and continuous Red / Blue / Purple team alignment.

---

## Platform Overview

| Component              | Details                                      |
|------------------------|----------------------------------------------|
| **Live Site**          | https://iscsecurity.org                      |
| **Hosting**            | Netlify                                      |
| **Membership / Paywall** | MemberSpace (`iscsecurity`)                |
| **Payments**           | Stripe (via MemberSpace)                     |
| **Lab Domain**         | `iscsecurity.local`                          |
| **Repository**         | This repo (GitHub → Netlify continuous deploy) |

---

## Access Model

| Page Type              | Visibility     | Notes                                      |
|------------------------|----------------|--------------------------------------------|
| Root / Module Indexes  | Public         | Structure and free samples visible to everyone |
| Lesson Pages           | Members-only   | Protected with `data-ms-content="members-only"` |
| Selected Intro Lessons | Public         | Intentional free samples for promotion     |

---

## Curriculum Structure (Ethical Hacking Track)

1. Introduction to Ethical Hacking  
2. Open Source Intelligence (OSINT)  
3. Footprinting & Reconnaissance  
4. Scanning Networks  
5. Enumeration  
6. Vulnerability Analysis  
7. System Hacking  
8. Malware Threats  
9. Network Sniffing & Traffic Interception  
10. Social Engineering
11. Denial of Service
12. Session Hijacking
13. Evading IDS/Firewalls & Honeypots
14. Hacking Web Servers
15. Hacking Web Applications
16. SQL Injection
17. Hacking Wireless Networks
18. Hacking Mobile Platforms
19. IOT/OT Hacking
20. Cloud Computing
21. Cryptography

Later tracks planned: Penetration Testing, SOC, Bug Bounty.

---

## Key Project Rules

- **Canonical World Bible** is the single source of truth for lab topology, hosts, credentials, and methodology.
- **Continuity doctrine**: Prior foothold is the SYSTEM shell on `AD-WIN10`. Do not invent implants or campaign state.
- **Release philosophy**: Fortnightly, production-ready modules only.
- All new pages must follow the page construction and callout standards defined in the World Bible.

---

## Local Development

```bash
# Clone the repository
git clone https://github.com/zanderson73/iscsecurity.git
cd iscsecurity

# Serve locally (example)
python3 -m http.server 8000
# or use any static server / Netlify CLI

Deployment

Primary branch: main
Netlify watches main and deploys automatically
Clean URLs are handled via the _redirects file
MemberSpace protection is applied at the page level (data-ms-content="members-only")


Important Files:
File / FolderPurpose1-CANONICAL-World-Bible.htmlSingle source of truth for the lab world_redirectsNetlify clean URL rules/content/1-ethical-hacking/All Ethical Hacking modules/css/styles.cssSite-wide styling

Contact & Community

Website: iscsecurity.org
Discussion: platform.cyberr.ai/groups/iscsecurity
GitHub: github.com/zanderson73


Authorization-first. Always.
