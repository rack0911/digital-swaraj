# Level 3: GAFAM Account Surgery (Stopping Big Tech Telemetry)

> ###  Time Required: 15 Minutes | Difficulty: Beginner | Workflow Disruption: Very Low
> 
> *Google, Meta, and Microsoft provide indispensable services, but their default configurations treat your personal communications, locations, and documents as commercial training data. In Level 3, we conduct account-level surgery: disabling telemetry pipelines and opting out of AI model training while preserving complete access to your essential digital accounts.*

---

## The 60-Second Action Plan

| Platform | Setting | Action to Take | Direct Result |
| :--- | :--- | :--- | :--- |
| **Google** | Web & App Activity | **Pause** or set Auto-Delete (3 Mo) | Stops logging search history, app launches, and assistant voice snippets. |
| **Google** | Google Timeline (Location History) | **Pause** & delete existing history | Stops compiling a searchable map of every physical trip, route, and stop you make. |
| **Gmail** | Smart Features & Personalization | Toggle **OFF** in Gmail Settings | Stops automated ML models from scanning incoming order receipts and invoices. |
| **Gmail App** | Un-uninstallable OEM system bloat | **Forward to Proton Mail** or use **Thunderbird** | Disables mobile Gmail app tracking; isolates or migrates legacy inbox to encrypted storage. |
| **LinkedIn** | Data for Generative AI Improvement | Toggle **OFF** in Data Privacy | Prohibits LinkedIn from using your profile, posts, and articles to train AI models. |
| **Meta** | Off-Meta Activity | **Disconnect Future Activity** | Stops third-party apps and websites from reporting your purchases back to Meta. |

---

> [!TIP]
> **Quick Takeaway:**
> If you already configured these settings from the table, **you are finished with Level 3.** 
> **[Jump straight to Level 4: The Disposable Identity](04_LEVEL_FOUR_IDENTITY_MASKING.md)** to implement email aliasing and password isolation. 
> *(Or scroll down for direct settings links and detailed step-by-step walkthroughs below.)*

---

## 1. Google Account Surgery: Halting the Permanent Dossier

Visit the central Google Activity dashboard while logged into your primary account: 
 **[myaccount.google.com/activitycontrols](https://myaccount.google.com/activitycontrols)**

### A. Web & App Activity
- **What It Logs by Default:** Every Google search query, every Android application you open on your phone, your Chrome browsing history, and audio recordings when voice search activates.
- **The Fix:**
 1. Click **Web & App Activity**.
 2. Click **Turn off** (select *Turn off* or *Turn off and delete activity*).
 3. If your workflow requires keeping it on, configure **Auto-delete** to **3 months** instead of the default 18 or 36 months.
 4. Uncheck the sub-setting: *"Include Chrome history and activity from sites, apps, and devices that use Google services."*

### B. Google Timeline (Location History)
- **What It Logs by Default:** A continuous, timestamped vector path of your physical movements throughout the day, including transport mode (walking, driving, transit).
- **The Fix:**
 1. Click **Timeline** (Location History).
 2. Click **Turn off**.
 3. Click **Delete old activity** to purge historical location points accumulated over past years.

### C. Personalized Advertising
Visit: **[myadcenter.google.com](https://myadcenter.google.com)**
- Toggle **Personalized ads** to **OFF**.
- This disables the assembly of interest graphs derived from your search and YouTube consumption.

---

## 2. Gmail Receipt Parsing: Turning Off "Smart Features"

As documented in Level 0, Google's backend intelligence scans confirmation emails, travel bookings, and tax invoices landing in your Gmail inbox.

### How to Turn It Off:
1. Open Gmail on the web (desktop browser recommended for account-wide enforcement).
2. Click the **Settings** gear icon in the top right ➔ **See all settings**.
3. Under the **General** tab, scroll down to find these two adjacent toggles:
 - **Smart features and personalization:** Controls automated features inside Gmail (e.g., package tracking cards, automated event creation).
 - **Smart features and personalization in other Google products:** Controls data sharing across Google Maps, Google Assistant, and Travel.
4. **Uncheck BOTH boxes.**
5. Scroll to the bottom of the page and click **Save Changes**.

**The Trade-Off:** 
You will no longer see automated "Track Package" interactive banners pinned above delivery emails, and flight confirmations won't automatically sync to Google Calendar. In exchange, your commercial receipts and booking PDFs are no longer ingested into Google's cross-product telemetry pipelines.

---

## 3. The Gmail Containment Strategy: Forwarding & Thunderbird

For most users in India, deleting a 10-year-old Gmail address is impractical—it is linked to college alumni portals, old utility accounts, and government registrations. Furthermore, on most Android devices, manufacturers lock the Gmail mobile app as a system application that **cannot be uninstalled**.

If you cannot immediately delete your Google account or uninstall the app, deploy one of these two battle-tested containment strategies:

### Strategy 1: Clean Client Isolation via [Thunderbird](https://www.thunderbird.net/) (Android & Desktop)
If you want to keep receiving and sending email from your current `@gmail.com` address without running Google's proprietary mobile app:
1. **Disable the Gmail App:** Go to phone **Settings ➔ Apps ➔ Gmail ➔ Disable** (and revoke all background permissions).
2. **Install Thunderbird:** Download the official open-source **[Thunderbird for Android](https://www.thunderbird.net/)** (available on F-Droid, Google Play, and GitHub—the official evolution of the renowned K-9 Mail project) or the Thunderbird desktop client.
3. **Connect via Standard IMAP:** Log in with your Gmail credentials using standard OAuth2 authentication.
4. **The Advantage:** You receive your mail through a 100% open-source client with zero telemetry, zero embedded inbox ads, and local open-source code handling your message rendering.

---

### Strategy 2: Automatic Forwarding to a Sovereign Inbox (Proton Mail / Tuta)
If you are ready to transition your daily communications to an end-to-end encrypted email provider:
1. Create a free sovereign email account with **[Proton Mail](https://proton.me/mail)** (Swiss jurisdiction) or **[Tuta](https://tuta.com/)** (German zero-knowledge architecture).
2. Open Gmail on your desktop browser ➔ **Settings (gear icon) ➔ See all settings ➔ Forwarding and POP/IMAP**.
3. Click **Add a forwarding address** and enter your new encrypted email address.
4. Confirm the verification code sent to your new inbox.
5. Select: **"Forward a copy of incoming mail to [your new email] and archive/delete Gmail's copy"**.
6. **The Advantage:** Any legacy bank, relative, or service sending mail to your old `@gmail.com` address is forwarded instantly to your encrypted inbox. You manage everything from your sovereign email app, completely removing Google's mobile app from your daily routine.

---

## 4. LinkedIn Data Privacy & AI Model Training Opt-Out

In 2024, LinkedIn quietly updated its privacy terms to automatically ingest user profile data, public posts, published articles, and platform interactions into datasets used to train its parent company's generative AI models.

### Step-by-Step Opt-Out:
1. Open LinkedIn ➔ Click your profile icon ➔ **Settings & Privacy**.
2. In the left navigation, click **Data privacy**.
3. Locate **Data for generative AI improvement**.
4. Toggle the switch to **OFF** (*"Turn off to opt out of having your personal data and content used to train generative AI models"*).

### Additional High-Value LinkedIn Privacy Toggles:
While in the **Data privacy** section:
- **Social actions that show your network:** Under *How LinkedIn uses your data*, set *"Pairing your social actions with ads"* to **No** (prevents your name and photo from appearing to your connections on sponsored corporate ads you liked).
- **Profile discovery using email / phone number:** Set both to **Nobody** or **1st-degree connections** to prevent recruiter aggregators from reverse-searching your profile using your phone number.

---

## 5. Meta (Facebook & Instagram): Disconnecting Off-Platform Tracking

Even if you browse shopping or service websites with your Instagram or Facebook app closed, third-party sites in India send your activity (items viewed, cart additions, purchases) back to Meta using the **Meta Business SDK / Pixel**.

### How to Disconnect Future Off-Meta Activity:
1. Open **Instagram** (or Facebook) ➔ Go to your Profile ➔ **Settings**.
2. Tap **Accounts Center** ➔ Under *Account settings*, tap **Your information and permissions**.
3. Tap **Your activity off Meta technologies**.
4. Tap **Disconnect future activity**.
5. Select **Disconnect future activity** and confirm.
6. Return to the previous screen and tap **Clear previous activity** to unlink past commercial transaction logs.

**The Technical Shift:** External websites and shopping portals can no longer tie your off-platform browsing back to your Meta user account.

---

## Completed Checklist

- [x] Google Web & App Activity paused or limited to 3-month auto-deletion.
- [x] Google Timeline (Location History) permanently paused and past history purged.
- [x] Google Personalized Advertising toggled OFF.
- [x] Gmail "Smart features and personalization" disabled across all services.
- [x] Gmail mobile app contained: disabled in favor of Thunderbird for Android or auto-forwarded to an encrypted inbox (Proton / Tuta).
- [x] LinkedIn generative AI training on personal profile data opted out.
- [x] Off-Meta activity tracking disconnected and historical logs purged.

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your accounts:

1. **Severed Historical Retention:** Google no longer appends every search query, app launch, and physical coordinate to a multi-year chronological ledger tied to your identity.
2. **Inbox Email Privacy Restored:** Incoming flight bookings, e-commerce invoices, and utility receipts in Gmail are no longer parsed by backend ML models to populate ecosystem-wide user profiles.
3. **Mobile App Telemetry Quarantined:** You no longer run Google's tracking-laden mobile email client; mail is either read through an open-source client (Thunderbird) or forwarded cleanly to an end-to-end encrypted inbox.
4. **Professional Profile Shielded:** Your resume details, career history, and published posts on LinkedIn are explicitly excluded from generative AI training pipelines.
5. **Third-Party Pixel Isolation:** Off-platform web purchases and shopping visits are disconnected from your social media identity, stopping cross-site ad re-targeting funnels.

---
**Support the Project:** Star this repository on GitHub to help other Indian developers, students, and citizens discover it.
**Proceed to [Level 4: The Disposable Identity](04_LEVEL_FOUR_IDENTITY_MASKING.md)**
