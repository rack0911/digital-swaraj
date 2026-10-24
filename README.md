# Digital Swaraj (India Edition)
### A Pragmatic Playbook for Digital Sovereignty in India

An open-source, level-by-level operational guide to reclaim your privacy, attention, and data autonomy from default smartphone tracking—engineered specifically for the Indian digital ecosystem.

---

> **Status:** Verified (Current as of October 2026)  
> **Technical Baseline:** Android 13/14/15, Linux Kernel 6.x, Chromium / Gecko (Firefox ESR)  
> **Regulatory Citations:** TRAI TCCCPR 2018, MoCA Advisory (May 23, 2023), RBI Digital Lending Guidelines 2022, UIDAI Aadhaar Act 2016, CERT-In Directions No. 20(3)/2022

---

> [!NOTE]
> **Zero-Sponsorship & Independence Declaration**
> None of the tools, browsers, operating systems, apps, or DNS resolvers recommended in this entire playbook are sponsored. There are **zero affiliate links, paid partnerships, or referral codes** anywhere in this repository. All recommendations are based strictly on open-source code audits, technical security standards, and privacy architecture.

---

## Why This Exists

Most privacy guides on the internet are written for users in North America or Europe. Their advice falls apart the moment you step onto an Indian street:

| Western Advice | Indian Reality |
| :--- | :--- |
| *"Just use cash everywhere."* | Cash is frequently refused for small transactions; UPI QR codes are the universal standard. |
| *"Delete WhatsApp and move to Signal."* | College departments, apartment associations, local utilities, and families run exclusively on WhatsApp. Dropping it cold-turkey causes complete social and operational friction. |
| *"Use disposable burner VoIP numbers."* | Indian telecom regulations mandate physical, Aadhaar-linked SIMs tied to device IMEI for banking and authentication. Virtual numbers are blocked. |
| *"Self-host your email server."* | Indian PSU bank portals (SBI, PNB, Canara) and government forms often use strict regex validators that break on non-standard email domains. |

**This playbook is engineered for Indian ground reality.**

It does not ask you to disconnect from modern society, become a paranoid hermit, or live without technology. Instead, it offers a pragmatic, step-by-step roadmap to systematically shut down invasive tracking, defang dark patterns, and regain control over your attention—without breaking the services you rely on every day.

---

## Adoption Paths: Choose Your Depth

Not every citizen needs to install a new desktop operating system or execute ADB commands to achieve meaningful privacy. The playbook is structured into three progressive operational profiles:

| Profile | Target Audience | Time Investment | Focus Areas |
| :--- | :--- | :--- | :--- |
| **Path A: The Pragmatic Citizen** | Everyday smartphone users, non-technical family members, students | **15 Minutes** (Zero Technical Skill) | Level 0 baseline audit awareness, Level 1 encrypted DNS (NextDNS/AdGuard DoT), Level 4 TRAI Full DND (SMS `START 0` to 1909), Level 6 statutory phone number refusal at retail counters. |
| **Path B: The Privacy-Conscious Mobile User** | Working professionals, privacy-aware individuals | **1 Hour** (No Root / No Coding) | Level 2 hardware radio/sensor containment, Level 3 GAFAM account surgery, Level 4 Three-Tier Email Architecture (Sovereign Vault + Managed Aliases), Level 5 Mobile FOSS suite (HeliBoard, Fossify, Aves Libre), Level 6 Masked Aadhaar. |
| **Path C: The Sovereign Engineer** | Developers, system administrators, advanced users | **Weekend Project** | Level 5 ADB non-root deep-daemon surgery, Level 7 Fedora Linux sovereign workstation, local document tools (Stirling-PDF, Squoosh, Flameshot), and Waydroid containerized messaging. |

---

## The Progression: Level 0 to Level 7
Take it one step at a time. Stop at whatever level matches your personal comfort and threat model.

```
[Level 0] The Default Trap (The Audit - What They Know While You Sleep)
   │
   ▼
[Level 1] The Zero-Effort Shield (Browser Hardening & Encrypted DNS)
   │
   ▼
[Level 2] Mobile Radio & Sensor Hygiene (Killing Phantom Trackers)
   │
   ▼
[Level 3] GAFAM Account Surgery (Taming Google & LinkedIn Telemetry)
   │
   ▼
[Level 4] The Disposable Identity (Email Aliasing & Credential Isolation)
   │
   ▼
[Level 5] The FOSS Mobile Stack (Clean Open-Source Replacements)
   │
   ▼
[Level 6] Street & FinTech Defense (Masked Aadhaar & Retail Rights)
   │
   ▼
[Level 7] The Sovereign Workstation (Desktop Sandboxing & Workstation Containment)
```

---

### Level Index

- **[Level 0: The Default Trap (What They Know While You Sleep)](levels/00_LEVEL_ZERO_THE_DEFAULT_TRAP.md)**  
  *The baseline audit.* How default configurations leak data through Xerox shop printouts, ₹10 UPI location locking, billing counter phone number harvesting, festive lucky-draw lead generation, and background radio polling.

- **[Level 1: The Zero-Effort Shield](levels/01_LEVEL_ONE_BROWSER_AND_DNS.md)**  
  *10-minute setup. Zero workflow changes.* Hardened browsers (Brave/Firefox), Firefox Containers, router & mobile encrypted DNS, and offshore zero-log VPNs under CERT-In (Mullvad/Proton).

- **[Level 2: Mobile Radio & Sensor Hygiene](levels/02_LEVEL_TWO_RADIO_AND_SENSOR_HYGIENE.md)**  
  *Hardware containment.* Disabling background Wi-Fi and Bluetooth probe scanning, revoking unnecessary sensor permissions, and auditing location access.

- **[Level 3: GAFAM Account Surgery](levels/03_LEVEL_THREE_ACCOUNT_SURGERY.md)**  
  *Auditing the big accounts.* Pausing Web & App activity, turning off Gmail automated receipt parsing, and opting out of LinkedIn AI training datasets.

- **[Level 4: The Disposable Identity](levels/04_LEVEL_FOUR_IDENTITY_MASKING.md)**  
  *Isolating your contact footprint.* Three-tier email architecture (Sovereign Vault, managed aliases, 10-minute burners like Emailnator), credential isolation (Bitwarden/Proton), and offline 2FA (Aegis).

- **[Level 5: The Mobile FOSS Stack](levels/05_LEVEL_FIVE_MOBILE_FOSS_STACK.md)**  
  *Clean daily tools & deep daemon surgery.* F-Droid, Aurora Store (anonymous Play Store), HeliBoard, LocalSend, Fossify suite, and neutralizing hidden Google & OEM background tracking daemons (call-log scrapers, always-on mic listeners) via ADB without rooting.

- **[Level 6: Street & FinTech Defense](levels/06_LEVEL_SIX_STREET_AND_FINTECH_DEFENSE.md)**  
  *Real-world consumer protocols.* Masked Aadhaar usage, citing Ministry of Consumer Affairs retail billing rights, direct bank UPI, and delivery parcel honey-token defense.

- **[Level 7: The Sovereign Workstation](levels/07_LEVEL_SEVEN_SOVEREIGN_WORKSTATION.md)**  
  *Complete desktop sovereignty.* Linux workstation hardening (Fedora), local office suites (LibreOffice / OnlyOffice), local document tools (Stirling-PDF / Squoosh), offline clipboard hygiene (CopyQ), and sandboxing WhatsApp via Waydroid.

---

## Core Principles

1. **Pragmatism Over Paranoia:** We live in the real world. You still need to book IRCTC tickets, receive UPI payments, and stay in touch with family. We build sensible barriers, not impractical prisons.
2. **Zero Commercial Incentives & Sponsorships:** None of the tools, browsers, apps, or DNS resolvers recommended in this entire playbook are sponsored. There are zero affiliate links, paid partnerships, or referral codes anywhere in this repository. All recommendations are based strictly on technical audits, open standards, and privacy architecture.
3. **Legally & Statutorily Grounded:** All critiques and consumer guidance are anchored in official government documentation—including directives from the **Ministry of Consumer Affairs**, the **CCPA Guidelines for Prevention of Dark Patterns (2023)**, **RBI Digital Lending Guidelines**, and **CERT-In**.
4. **Accessible Engineering:** Clear, direct explanations that any smartphone user can understand and implement immediately.

---

## Public Interest & Legal Notice

This repository is maintained for educational and digital consumer awareness purposes under **Article 19(1)(a)** and **Article 21 (Right to Privacy)** of the Constitution of India (*Justice K.S. Puttaswamy (Retd.) v. Union of India*, 2017).

All referenced product names, trademarks, and registered marks belong to their respective holders. They are used purely for descriptive, educational, and nominative identification purposes under **Section 30 of the Trade Marks Act, 1999**.

---

## Support the Project
If this playbook helped you regain even 10% of your peace of mind or taught you something new:
- **Star this repository** to help other Indian developers, students, and citizens discover it.
- **Share it** with friends, colleagues, or family members who are overwhelmed by notification spam and intrusive defaults.

---

## Contributing

Discover a new dark pattern in an Indian app or a practical workaround that respects local constraints? Contributions are welcome via Pull Requests. Please review our guidelines to ensure recommendations remain accessible, legal, and verified.
