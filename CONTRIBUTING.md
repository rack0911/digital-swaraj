# Contributing to Digital Swaraj

Thank you for your interest in contributing to the **Digital Swaraj (India Edition)**. 

This repository is maintained as an open-source, non-commercial public interest guide designed to help Indian developers, students, and citizens protect their digital privacy and consumer autonomy.

We welcome contributions from researchers, privacy advocates, legal scholars, and engineers. To ensure this playbook remains accurate, accessible, and legally protected, all contributions must strictly adhere to the guidelines below.

---

## Core Contribution Standards

### 1. Zero Commercial Incentives
- **Strictly No Affiliate Links:** Any Pull Request introducing affiliate links, sponsored referral codes, or commercial tracking parameters will be closed immediately.
- **No Proprietary Upselling:** We do not recommend proprietary paid privacy services when free, audited, and open-source alternatives exist.

### 2. Legal & Factual Rigor
- **No Unverified Brand Defamation:** Do not submit generalized accusations against specific corporate entities. 
- **Anchor Claims in Official Regulations:** Any claimed dark pattern, regulatory violation, or consumer right must cite official Indian statutory frameworks, including:
  - **Ministry of Consumer Affairs** directives and consumer advisories.
  - **Central Consumer Protection Authority (CCPA)** Guidelines for Prevention and Regulation of Dark Patterns (2023).
  - **Reserve Bank of India (RBI)** Circulars and Digital Lending Guidelines.
  - **Unique Identification Authority of India (UIDAI)** Aadhaar circulars and regulations.
  - **CERT-In** cybersecurity alerts and technical advisories.

### 3. Pragmatism Over Paranoia
- Recommendations must be functional within the real-world Indian technical landscape:
  - Acknowledge UPI and NPCI requirements rather than preaching "cash only."
  - Account for Indian bank Core Banking Systems (Finacle) regex limitations when recommending email hygiene.
  - Respect telecom device-level binding regulations instead of recommending non-working foreign VoIP proxies.

### 4. Language & Tone Standard
- **Pure English Only:** To keep this playbook universally accessible across all Indian states and international audiences, all content must be authored in clear, professional English without regional transliterations or slang.
- **Concise & Actionable:** Follow the established format:
  - 60-Second Action Plan table at the top.
  - Fast-track jump links for quick readers.
  - Strict 3-bullet breakdowns (The Habit ➔ The Extraction ➔ The Reality/Risk).
  - Empirically verified claims only (no exaggerated marketing multipliers).

---

## How to Submit Contributions

### Reporting a New Dark Pattern
If you discover a pervasive dark pattern in an Indian application, open an Issue titled `[Dark Pattern]: <Description>` and include:
1. **The Application / Workflow:** Where the pattern occurs.
2. **The Mechanism:** What data is captured or what user choice is bypassed.
3. **The Regulatory Angle:** Which specific CCPA, Consumer Affairs, or RBI guideline addresses it.
4. **The Pragmatic Workaround:** How a consumer can bypass or mitigate it without breaking core functionality.

### Proposing a FOSS Alternative
If you wish to recommend an open-source tool, ensure it meets these criteria:
- Source code is publicly available under an OSI-approved open-source license.
- The software contains **zero embedded advertising SDKs or third-party telemetry**.
- Ideally available on **F-Droid** or official reproducible releases.

### Submitting Pull Requests
1. Fork the repository.
2. Create a clean branch: `git checkout -b fix/level-update`.
3. Ensure your Git author identity uses an anonymous/noreply email to safeguard your own privacy.
4. Submit your Pull Request with a clear summary of the changes and references.

---

Thank you for helping build an independent, privacy-conscious digital ecosystem in India! 🇮🇳
