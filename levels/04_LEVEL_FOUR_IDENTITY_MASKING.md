# Level 4: The Disposable Identity (Email Aliasing, Phone Hygiene & Credential Isolation)

> **Document Status:** Verified (Current as of October 2026)  
> **Supported Platform Scope:** Android (Aegis / Bitwarden / Proton Pass), iOS, Web Browsers, Indian Cellular Networks (Jio, Airtel, Vi, BSNL)  
> **Primary Technical & Regulatory Citations:** [TRAI TCCCPR 2018 Gazette Notification](https://trai.gov.in/sites/default/files/Regulation_19072018.pdf), [TRAI National Customer Preference Register Specification](https://trai.gov.in/faqcategory/national-customer-preference-register-ncpr), [RFC 6238 (TOTP Algorithm)](https://datatracker.ietf.org/doc/html/rfc6238), [RFC 9807 (OPAQUE Protocol)](https://datatracker.ietf.org/doc/html/rfc9807)

---

> **Level Goal:** Decouple your real contact identity from the commercial internet. If a service is breached, only a throwaway alias is exposed—while your real email, phone number, and master credentials remain invisible.

---

### The Reality Check (60-Second Overview)

| Vector | Current Vulnerable Default | The Zero-Effort Fix | Result |
| :--- | :--- | :--- | :--- |
| **Email Address** | Giving out primary personal email everywhere | **Email Aliasing & Burners** (DuckDuckGo / Proton / Emailnator) | Generate disposable aliases and ephemeral inboxes; cut down spam and isolate breaches. |
| **Banking Email** | Using custom domains on PSU bank portals | Keep one clean primary email strictly for banks | Prevents Finacle / Core Banking regex validation errors on official records. |
| **Mobile Number** | Surrendering real number to commercial databases | **TRAI Full DND (Category 0)** & 1909 Enforcement | Legally blocks commercial telemarketing; triggers statutory blacklisting for violators. |
| **Passwords** | Reusing 2–3 password variations | **Bitwarden** or **Proton Pass** | Generates unique 16+ character passwords with zero-knowledge encryption. |
| **2FA Verification** | Plaintext SMS OTPs (vulnerable to SIM swap) | **Aegis Authenticator** (Offline FOSS TOTP) | Generates offline time-based codes on your device without telecom network reliance. |

---

> [!TIP]
> **Quick Takeaway:** 
> If you already configured email aliasing, statutory DND, and an open-source password manager, **you are finished with Level 4.** 
> [Jump straight to Level 5: The Mobile FOSS Stack](05_LEVEL_FIVE_MOBILE_FOSS_STACK.md) to replace bloatware with clean open-source mobile tools. 
> *(Or scroll down to follow the setup guides and statutory enforcement protocols below.)*

---

## 1. Disposable Email Aliasing

Whenever an app, retail website, newsletter, or public forum asks for your email address, **never provide your real personal address.** 

Your primary email address is your master digital passport. Once data brokers, marketing crawlers, or breached databases link your real email to your phone number and full name, your personal inbox is flooded with targeted phishing, telemarketing, and spam.

### How Managed Email Aliasing Works
Instead of giving out your real address, deploy an **Email Aliasing Service**. It acts as an intelligent privacy shield between your real inbox and the outside world:
1. **On-Demand Aliases:** When a website asks for an email, generate a unique, throwaway alias on the fly (e.g., `shop9274@duck.com` or `order.831@passmail.net`).
2. **Tracker Stripping:** Incoming emails sent to the alias are received by the aliasing service, stripped of embedded tracking pixels and spyware beacons, and cleanly forwarded to your real primary inbox.
3. **Instant Deactivation:** If a merchant begins spamming you or sells your address to data brokers, click **"Deactivate Address"** in the email header or web dashboard. That alias is deactivated, stopping future incoming messages while keeping your real email address unexposed.

---

### Verified Managed Aliasing Tools

| Tool | Default Format | Best For | Key Strengths |
| :--- | :--- | :--- | :--- |
| **[DuckDuckGo Email Protection](https://duckduckgo.com/email/)** | `@duck.com` | Standalone setup across any browser | Free tier with unlimited alias generation, email spy pixel stripping, works with any inbox. |
| **[Proton Pass / SimpleLogin](https://proton.me/pass)** | `@passmail.net` / `@simplelogin.com` | Integrated password manager + email masks | Generates password and alias simultaneously, open-source, Swiss privacy laws, optional PGP encryption. |
| **[Brave Email Aliases](https://brave.com/)** | Native dummy forwarding | Native Brave Browser users | Built directly into Brave settings; zero third-party extensions required; uses OPAQUE zero-knowledge auth. |
| **[Addy.io](https://addy.io/)** *(formerly AnonAddy)* | `@anonaddy.me` or custom handle | Open-source purists & power users | Verified open-source (MIT), self-hostable, granular recipient rules, and custom domain support. |

#### Detailed Breakdown of Each Option:

#### Option A: [DuckDuckGo Email Protection](https://duckduckgo.com/email/) (Zero-Friction & Standalone)
- **Format:** `@duck.com`
- **How It Works:** DuckDuckGo provides a free `@duck.com` forwarding address that forwards to your existing Gmail, Outlook, or personal inbox.
- **Tracker Stripping:** Detects and removes hidden tracking pixels from corporate newsletters before forwarding messages to your real inbox.
- **Browser & Mobile Integration:** Built into DuckDuckGo browser extension on desktop and mobile apps; generates aliases directly inside input forms.
- **Deactivation:** Every forwarded email features an instant deactivation link right at the top of the message.

#### Option B: [Proton Pass / SimpleLogin](https://proton.me/pass) (Integrated Credential Vault)
- **Format:** `@passmail.net` or `@simplelogin.com`
- **How It Works:** Built directly into the Proton Pass password manager (powered by SimpleLogin, acquired by Proton).
- **All-in-One Workflow:** Whenever you register on a new site, Proton Pass generates a strong 16-character password and a unique masked email in a single click.
- **Cryptographic Security:** End-to-end encrypted with open-source audited code; supports forward-to-PGP encryption so intermediate email servers cannot inspect your mail.

#### Option C: [Brave Email Aliases](https://brave.com/) (Native Browser Integration)
- **Format:** Managed disposable addresses
- **How It Works:** Integrated directly into the Brave browser settings using a privacy-preserving Brave Account.
- **Zero Extensions:** Requires no third-party extensions or separate add-on software if Brave is already your primary browser.
- **Zero-Knowledge Architecture:** Authenticated using the **OPAQUE** protocol (RFC 9807), meaning your account password and authentication keys are never transmitted to server infrastructure.

#### Option D: [Addy.io](https://addy.io/) (Open-Source Community Standard)
- **Format:** `@anonaddy.me` or your own custom domain
- **How It Works:** An independent, open-source email forwarding service built specifically for user autonomy.
- **Granular Control:** Offers full control over send/reply headers, multiple recipient destinations, and custom domain mapping.
- **Self-Hostable:** Can be run on your own private server if you require complete infrastructure independence.

---

### Ephemeral Burners: 10-Minute Mail & Emailnator (Zero-Stakes Inboxes)

For websites where you **never want to receive an email again**:
- Downloading a free eBook or whitepaper gated behind an email submission.
- Reading a single forum post locked behind a mandatory registration wall.
- Claiming a one-time signup discount code on a suspicious retail site.
- Testing an untrusted web application.

For these situations, even a managed `@duck.com` or Proton alias creates unnecessary storage overhead because confirmation emails still reach your primary inbox. Instead, deploy an **Ephemeral Burner Inbox**.

#### How Burner Inboxes Differ from Aliases:
- **Zero Forwarding:** Burner inboxes do *not* forward mail to your inbox. The entire inbox lives temporarily inside a browser tab.
- **Auto-Destruction:** After 10 to 60 minutes, the temporary mailbox and all received emails self-destruct permanently.
- **Zero Account Clutter:** Copy the burner address, paste it on the website, read the verification link or OTP in the burner tab, and close the browser.

#### Verified Burner Services:
1. **[Emailnator](https://www.emailnator.com/) (Best for Bypassing Blocks):** Many corporate websites actively block generic `@temp-mail` domains. Emailnator solves this by generating temporary disposable `@gmail.com` addresses (leveraging Gmail dot and plus variations), allowing you to bypass strict sign-up filters.
2. **[10MinuteMail](https://10minutemail.com/):** The classic, countdown-based disposable inbox. Generates a fresh random address that auto-deletes in 10 minutes (extendable with a single click if needed).
3. **[Temp-Mail](https://temp-mail.org/):** Instant disposable web inbox with automated real-time incoming message refreshes.

> [!WARNING]
> **The Golden Safety Rule:** 
> **Never** use a 10-minute burner email for accounts requiring long-term access (financial accounts, password managers, flight bookings, or services holding personal data). If you forget your password or need a 2FA recovery code next month, that burner address cannot be recovered.

---

## 2. The Indian Banking & Government Exception

A common mistake made by privacy enthusiasts in India is attempting to use email aliases or custom domains for everything—including their bank accounts.

### The Finacle / Core Banking Reality
Most Indian Public Sector Undertaking (PSU) banks (SBI, Canara, PNB) and government portals (Income Tax, EPFO, Passport Seva) run legacy Core Banking Systems (CBS) like Infosys Finacle. 

These legacy portals often feature rigid input validation regexes:
- They frequently reject newer top-level domains (TLDs like `.me`, `.xyz`, or `.io`).
- Forwarded aliases can occasionally trigger anti-fraud flags or fail automated verification loops.

### The Three-Tier Email Architecture
To prevent critical transaction alerts or tax communications from breaking while keeping your personal inbox clean, split your digital footprint into three distinct tiers:

```
[Tier 1: Sovereign Vault Email] ─────────► Strictly for: Bank Accounts, EPFO, 
(Your Clean, Primary Email) Income Tax, Demat/Trading, Passport Seva.
                                            (Never used for shopping, apps, or social media).

[Tier 2: Managed Aliases] ─────────► Used for: Amazon, Flipkart, Swiggy, Zomato,
(DuckDuckGo / Proton / Addy.io) Newsletters, Forums, Shopping Apps, Utilities.
                                            (Deactivated instantly if spammed or breached).

[Tier 3: 10-Minute Burner Inboxes] ───────► Used for: Gated PDF Downloads, Single-Use OTPs,
(Emailnator / 10MinuteMail) Forced Signup Walls, Testing Untrusted Websites.
                                            (Self-destructs completely; zero inbox clutter).
```

---

## 3. Mobile Number Hygiene & Statutory DND Enforcement (TRAI Category 0)

Western privacy guides frequently recommend purchasing "disposable burner SIMs" with cash. In India, this is technically and legally impossible: the Department of Telecommunications (DoT) mandates biometric Aadhaar e-KYC and device IMEI binding for every cellular connection. 

Because your mobile number functions as India's universal financial identifier, commercial telemarketers, loan aggregators, and data scrapers aggressively target active numbers. The sovereign defense is not living off-grid, but invoking your statutory rights under Indian telecom law.

### Step 1: Activate TRAI Category 0 (Full DND)
Under the **Telecom Commercial Communications Customer Preference Regulations (TCCCPR, 2018)** issued by the Telecom Regulatory Authority of India (TRAI), telemarketers are legally prohibited from transmitting commercial calls or SMS to registered numbers.

Activate Full DND using any of these three standardized methods:

1. **SMS Method (10 Seconds):** 
 Send an SMS with the text **`START 0`** to **`1909`** (free and standardized across **Jio, Airtel, Vodafone Idea, and BSNL**).
2. **Call Method:** 
 Dial **`1909`** from your phone and follow the automated IVR prompts to register for *Full DND / Total Blocking (Category 0)*.
3. **Telecom App Method:** 
 Open your telecom operator's app (*MyJio*, *Airtel Thanks*, or *Vi*): 
 Navigate to **Settings / Preferences ➔ Do Not Disturb (DND) ➔ Select Fully Blocked (Category 0)**.

Once registered, telecom operators are statutorily required to enforce the block within 24 hours.

---

### Step 2: The Regulatory Enforcement Weapon (The 1909 Reporting Loop)
If an unregistered telemarketer or commercial agent calls or messages you after DND registration, you have the statutory power to trigger regulatory penalties against them:

1. Within **3 days** of receiving an unsolicited spam call or SMS, send an SMS to **`1909`** in the exact statutory format: 
 `COMP TEL NO <Spammer Number>, dd/mm/yy, Brief description` 
 *(Example: `COMP TEL NO 9876543210, 24/10/24, unsolicited personal loan call`)* 
 Alternatively, file the complaint directly via the official **TRAI DND 3.0** app.
2. **The Legal Consequence:** Under TCCCPR regulations, your telecom provider must investigate within 30 days. On verified violations:
 - First offense: The telemarketer receives a formal notice and monetary penalty.
 - Repeated violations: The telecom provider is statutorily required to **disconnect all telecom connections and permanently blacklist** the offending individual or entity across all Indian cellular networks.

---

## 4. Credential Isolation: Password Management (Bitwarden / Proton Pass)

Reusing passwords across websites is the number-one cause of account takeovers in India. When a regional merchant or ticketing portal suffers a database leak, credential-stuffing bots immediately test that same email/password combination on major services.

### Option A (Gold Standard): [Bitwarden](https://bitwarden.com/) (Open-Source & Audited)
- **Core Security:** Fully open-source, end-to-end encrypted with zero-knowledge architecture (Bitwarden cannot read your vault even under subpoena).
- **Free Tier:** Complete cross-platform syncing across Linux, Windows, Android, and iOS.
- **Workflow:** Remember **one strong master passphrase**. For every website registered, Bitwarden generates a random 16+ character password (e.g., `8vQ#mK2$pL9!xZ4`).
- **Autofill:** Integrates natively into Android autofill and mobile browsers for one-tap biometric logins.

### Option B (Modern Beginner Alternative): [Proton Pass](https://proton.me/pass)
- **Built-in Email Aliases:** Integrated directly with SimpleLogin (acquired by Proton). Generate unique email aliases and passwords simultaneously in a single tap without needing separate tools.
- **User Experience:** Sleeker, highly polished mobile interface ideal for non-technical users.
- **Zero-Knowledge Encryption:** Audited open-source cryptography backed by Swiss privacy protections.

---

## 5. Two-Factor Authentication (2FA) Hygiene: Moving Beyond SMS

In India, SMS OTPs are the default two-factor authentication method. However, SMS is fundamentally insecure:
- **Plaintext & Interceptable:** SMS travels over unencrypted telecom channels, vulnerable to SS7 cellular protocol exploits and rogue telecom tower sniffing.
- **SIM Swap Fraud:** Attackers routinely use forged documents or corrupt store clerks to execute SIM swap attacks, instantly rerouting all your incoming OTPs to an attacker's phone.
- **Android Malware Interception:** Fraudulent APKs with Android's `READ_SMS` permission can intercept authentication OTPs in the background without user intervention.

Whenever an online service (Google, GitHub, Bitwarden, Amazon, social media, crypto exchanges) offers an **"Authenticator App"** or **"TOTP" (Time-based One-Time Password)** option, disable SMS and switch to app-based codes.

---

### Recommended Privacy-First Tools

#### The Recommended Standard: [Aegis Authenticator](https://getaegis.com/) (Android FOSS)
- **Offline by Design:** Aegis does not declare the `android.permission.INTERNET` permission in its Android manifest. The operating system sandbox prevents the app from establishing network connections, ensuring 2FA seeds remain strictly on local storage.
- **Biometric & Encrypted Vault:** Your TOTP tokens are stored on your device inside an AES-256-GCM encrypted database unlocked via your fingerprint or PIN.
- **Secure Local Backups:** Allows exporting an encrypted backup file to local storage or an SD card. When switching phones, simply restore the file—no cloud accounts required.
- *(For iOS / Multi-Device Sync: Consider **[Ente Auth](https://ente.io/auth/)**, a verified open-source, end-to-end encrypted cross-platform alternative).*

---

### Mainstream Big Tech Apps (Why They Are Not Recommended)

- **Google Authenticator & Microsoft Authenticator:**
 - **The Privacy Trade-off:** While ubiquitous, Google and Microsoft embed proprietary telemetry into these apps and push automatic cloud-sync to your Google / Microsoft corporate account.
 - **Identity Centralization:** Syncing your 2FA seeds to Google or Microsoft ties your independent second-factor verification directly into Big Tech's identity graph. If your Google or Microsoft account is locked, flagged, or suspended, you lose access to all your 2FA tokens simultaneously.
 - **Verdict:** For true digital sovereignty and zero tracking, avoid proprietary Big Tech authenticators.

---

### Integrated Password Manager 2FA (Bitwarden & Proton Pass)

Both major privacy password managers can store TOTP seeds and generate 2FA codes directly alongside your passwords, but keep these financial and architectural trade-offs in mind:

- **Bitwarden:**
 - Integrated TOTP autofill is an efficient workflow (it automatically copies your 2FA code to your clipboard upon autofilling your password).
 - **Pricing Detail:** On the official Bitwarden cloud service, integrated TOTP storage is a premium feature requiring approximately **~$10/year (~$1–2 per month)** at the time of writing. If you self-host your own server (using [Vaultwarden](https://github.com/dani-garcia/vaultwarden)), integrated TOTP is included at no extra license fee.
- **Proton Pass:**
 - Integrated 2FA code generation is available within the Proton ecosystem (included under Proton Pass Plus / Unlimited subscriptions).

> [!WARNING]
> **The Security Trade-Off: Convenience vs. Compartmentalization** 
> Storing both your master password and your 2FA secret seed in the same password manager means a single compromised master password gives an attacker access to *both* authentication factors. 
> **Recommended Best Practice:** Keep high-value accounts (your primary email vault, password manager master account, and primary financial tools) isolated inside a standalone offline authenticator like **Aegis**.

---

## Technical Boundaries & Limitations of Level 4

* **Email Aliasing Provider Reliance:** Utilizing an aliasing service (DuckDuckGo, SimpleLogin/Proton Pass, Addy.io) introduces an intermediary forwarder into your communications architecture. If the provider experiences downtime or technical latency, critical verification emails may be delayed. Furthermore, if your master aliasing account is compromised or locked, inbound routing across all associated masks is interrupted.
* **Email Transit Encryption Limits:** Email masks strip embedded tracking beacons and forward clean messages. However, transit from the original merchant to the alias provider occurs over standard SMTP with opportunistic STARTTLS in cleartext to the provider's MX server. To achieve cryptographic privacy at rest, configure PGP public-key encryption on your aliasing dashboard so inbound emails are encrypted before forwarding.
* **Email Aliasing vs. Physical Delivery Records:** While email masks strip tracking pixels and prevent your master address from leaking in merchant database breaches, they **cannot conceal your physical shipping address, real name, or payment card billing details** entered on checkout pages.
* **TRAI DND vs. Unregistered Telemarketers (UTMs):** Activating TRAI Category 0 Full DND under [TRAI TCCCPR 2018](https://trai.gov.in/sites/default/files/Regulation_19072018.pdf) legally binds all 2.5+ lakh registered telemarketers (Principal Entities) operating over 140-series sender headers. However, **unregistered rogue entities calling from personal 10-digit SIM cards** bypass automated carrier filters. Remediation requires filing a statutory complaint via SMS `COMP TEL NO ...` to 1909 or the TRAI DND 3.0 app within 3 days to initiate telecom carrier blacklisting.
* **Burner Inboxes vs. Session Expiry & Recovery:** 10-minute temporary inboxes (Emailnator, 10MinuteMail) do not retain history. If an account requires ongoing password resets, account verification, or financial recovery, using an ephemeral burner leads to permanent account loss.
* **App-Based TOTP vs. Cold Backups:** Offline authenticators (Aegis, Ente Auth) eliminate SMS interception risks. However, if a user loses their phone without keeping an encrypted backup export of their TOTP secret seeds (stored on offline cold media or personal cloud backup), recovering those accounts requires service-specific fallback procedures.

---

## Completed Checklist

- [x] Managed disposable email aliasing (DuckDuckGo, Proton Pass, Brave, or Addy.io) configured for throwaway addresses.
- [x] Ephemeral burner inboxes (Emailnator / 10MinuteMail) bookmarked for zero-stakes gated downloads and forced signup walls.
- [x] Three-Tier Email Architecture established (Sovereign Vault for banking; managed aliases for apps; 10-minute burners for throwaways).
- [x] TRAI Full DND (Category 0) activated on primary SIM via SMS `START 0` to 1909.
- [x] Open-source password manager (Bitwarden or Proton Pass) installed with unique, strong passwords generated for all accounts.
- [x] Critical online accounts migrated to offline TOTP two-factor authentication via Aegis or an encrypted authenticator.

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your identity:

1. **Breach Compartmentalization:** If an online retailer or food delivery service suffers a database leak, the exposed email is a disposable alias and the password is unique. Your other accounts and real email address remain completely secure.
2. **One-Click Spam Termination:** Unwanted marketing broadcasts can be stopped by deactivating the specific alias without needing to interact with suspicious unsubscribe links.
3. **Zero Inbox Clutter from One-Offs:** Downloading whitepapers or reading gated articles leaves zero trace in your inbox—the burner address self-destructs within minutes.
4. **Statutory Telemarketing Defense:** Your phone number is registered on TRAI Category 0 Full DND, creating legal liability and disconnection risks for unsolicited telemarketers.
5. **Legacy Portal Stability:** Your critical banking, tax, and government notifications remain fully operational on standard portals without regex validation errors.
6. **Offline Authentication Resiliency:** Two-factor authentication codes generate locally on your phone without waiting for delayed SMS network deliveries.

---
> **Reporting Inaccuracies or Changed Regulations:**  
> Have you identified an updated TRAI regulation, a modified DND registration code, or an issue with an aliasing provider? [Open an issue on GitHub](https://github.com/rack0911/digital-swaraj/issues).

---
[Proceed to Level 5: The Mobile FOSS Stack](05_LEVEL_FIVE_MOBILE_FOSS_STACK.md)
