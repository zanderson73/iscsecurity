# ISCSECURITY – WebPage Build (Final)

Static HTML training platform for **ISC Security** (iscsecurity.org).  
Authorization-first ethical hacking curriculum with public indexes, selective free samples, and members-only full lessons.

---

## Overview

This repository contains the production static site for the ISCSECURITY Master Class Series.

- **Live site**: [https://iscsecurity.org](https://iscsecurity.org)
- **Lab domain**: `iscsecurity.local` (reference topology only)
- **Hosting**: Netlify
- **Membership / Paywall**: MemberSpace (`iscsecurity` subdomain)
- **Payments**: Stripe (via MemberSpace)

The platform delivers structured ethical hacking training with strong emphasis on continuity, realistic lab mapping, Red/Blue/Purple team perspectives, and production-ready fortnightly releases.

---

## Tech Stack

| Layer              | Technology                                    |
|--------------------|------------------------------------------------|
| Site               | Static HTML + CSS                              |
| Hosting            | Netlify                                        |
| Membership         | MemberSpace (`data-ms-content="members-only"`) |
| Payments           | Stripe (linked through MemberSpace)            |
| Redirects          | Netlify `_redirects`                           |
| Versioning         | GitHub                                         |

---

## Access Model

| Page Type              | Visibility     | Notes                                              |
|------------------------|----------------|----------------------------------------------------|
| Root / Content / Module Indexes | Public        | No membership required                     |
| Lesson pages           | Members-only   | Protected with `data-ms-content="members-only"`    |
| Selected intro lessons | Public         | Intentional free samples for promotion             |

---

## Repository Structure (High Level)

```text
/
├── content/
│   └── 1-ethical-hacking/          # Clean URLs (production)
│       ├── 1-introduction-to-ethical-hacking/
│       ├── 2-open-source-intelligence/
│       ├── 3-footprinting-and-recon/
│       ├── 4-scanning-networks/
│       ├── 5-enumeration/
│       ├── 6-vulnerability-analysis/
│       ├── 7-system-hacking/
│       └── 8-malware-threats/
├── css/
├── images/
├── js/
├── _redirects                      # Netlify path normalization (.html ↔ clean)
└── 1-CANONICAL-World-Bible.html    # Single source of truth
```

> 💡 **Note**: Source files may exist under `2-ethical-hacking/` during development. Production clean URLs and redirects point to `1-ethical-hacking/`.

---

## Key Conventions

### 1. Canonical World Bible
`1-CANONICAL-World-Bible.html` is the **single authoritative source** for:
- Network topology (`192.168.56.0/24` external, `172.16.5.0/24` internal)
- Canonical hosts (Kali, AD-WIN10, DC01, SQL01, WEB01, CLIENT01, APP01)
- Operator methodology
- Continuity rules
- Callout system
- Page construction standards

**Every new page must inherit from the World Bible.**

### 2. Continuity Rule (Critical)
- Prior foothold state must be respected.
- Do **not** invent prior malware implants or campaign state.
- Credit techniques to the module where they were actually established.

### 3. Callout Classes

| Class                  | Purpose                          |
|------------------------|----------------------------------|
| `.reminder`            | Red Team / adversarial notes     |
| `.info-remember`       | Blue Team / detection            |
| `.redblue-reminder`    | Purple Team synthesis            |
| `.reminder-auth`       | Authorized-use legal banner      |
| `.reminder-comp`       | International compliance         |
| `.reminder-lab`        | Lab environment notice           |
| `.reminder-opsec`      | OPSEC caveats                    |
| `.reminder-lightblue`  | Gateway criteria                 |

### 4. Release Philosophy
- Fortnightly, production-ready modules only.
- Prefer solid, current drops over large unfinished dumps.

---

## Development Workflow

1. Work on feature branches.
2. Keep pages aligned with the Canonical World Bible.
3. Validate:
   - Continuity statements
   - IP addresses / hostnames
   - Callout usage
   - MemberSpace protection on lesson pages
4. Update `_redirects` when adding new pages.
5. Open a Pull Request for review before merging to main.
6. Netlify auto-deploys from the main branch.

---

## MemberSpace Integration

Lesson pages include the required subdomain initialization scripts and core layout tags:

```html
<script>
  window.MemberSpace = window.MemberSpace || { subdomain: "iscsecurity" };
  // ...
</script>

<!-- Content pages must leverage the access tag to trigger enforcement -->
<main data-ms-content="members-only">
  <!-- Restricted lesson content here -->
</main>
```

*Note: All category, index, and course syllabus pages remain completely public to preserve SEO visibility.*

---

## Current Curriculum Spine (Ethical Hacking Track)

| Module | Status |
| :--- | :--- |
| **1. Introduction to Ethical Hacking** | Complete |
| **2. OSINT** | Complete |
| **3. Footprinting & Reconnaissance** | Complete |
| **4. Scanning Networks** | Complete |
| **5. Enumeration** | Complete |
| **6. Vulnerability Analysis** | Complete |
| **7. System Hacking** | Complete |
| **8. Malware Threats** | Complete (Recently Finalized) |

*Later tracks (Penetration Testing, SOC, Bug Bounty) currently display placeholder indexes.*

---

## Contributing

1. Follow the Canonical World Bible and continuity rules strictly.
2. Maintain consistent Red / Blue / Purple callout structure.
3. Keep all lab examples inside the documented topology.
4. Do not invent prior campaign state.
5. Test MemberSpace protection tags and clean URL redirects before merging code.

---

## License & Authorization

All content is for educational and defensive training purposes only. Unauthorized use of the techniques described within these modules may violate local and 
international laws. Always obtain explicit, signed, written authorization before testing any production environment or infrastructure.

**ISC Security**  
*Authorization-first training.*  
[https://iscsecurity.org](https://iscsecurity.org)
