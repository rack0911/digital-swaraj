# Level 5: The Mobile FOSS Stack (Clean Open-Source Replacements)

> **Document Status:** Verified (Current as of October 2026)  
> **Supported Device Scope:** Android 12, 13, 14, 15 (Stock/Pixel, Samsung One UI 5/6, Xiaomi MIUI 14 / HyperOS, ColorOS/OxygenOS 13/14, Vivo Funtouch OS 13/14, Nothing OS 2.5/3.0); ADB Platform-Tools 35+  
> **Primary Technical Citations:** [Android Developer: SmsRetriever API](https://developers.google.com/identity/sms-retriever/overview), [Android Developer: AppOpsManager](https://developer.android.com/reference/android/app/AppOpsManager), [Android Developers: Play Integrity API](https://developer.android.com/google/play/integrity), [AOSP Package Management](https://source.android.com/docs/core/permissions/runtime_perms)

---

> ###  Time Required: 15 Minutes | Difficulty: Intermediate | Workflow Disruption: Low
> 
> *The average smartphone in India comes pre-loaded with proprietary utilities: keyboards that transmit keystroke telemetry to cloud servers, gallery apps with full-screen banner ads, dialers that sync call logs, and file-sharing utilities riddled with bloatware. In Level 5, we replace these daily tools with clean, lightweight Free and Open Source Software (FOSS) that respects your privacy and contains zero advertising.*

---

## The 60-Second Action Plan

| Vector | Bloated Proprietary Default | The FOSS Replacement | Direct Result |
| :--- | :--- | :--- | :--- |
| **App Store (FOSS)** | Google Play Store (exclusively) | **F-Droid** | Access verified, tracking-free open-source mobile software. |
| **App Store (Proprietary)** | Google Play logged into personal Gmail | **Aurora Store** | Anonymous Play Store client; downloads genuine APKs without a Google account. |
| **Keyboard** | Gboard / SwiftKey | **HeliBoard** | Offline typing; compiled without network permissions, preventing cloud keystroke synchronization. |
| **Local File Share** | SHAREit / Quick Share / Nearby | **LocalSend** | Encrypted peer-to-peer file transfer over local Wi-Fi across Android, PC, and iOS. |
| **Video Streaming** | YouTube App (heavy ads & tracking) | **NewPipe** or **Brave Browser** | Ad-free viewing, background audio playback, zero Google account required. |
| **Photo Gallery** | Proprietary OEM Gallery with ads | **Aves Libre** | Fast, clean, offline media management with full metadata and EXIF control. |
| **Cloud Photo Backup** | Google Photos (facial recognition & indexing) | **Ente Photos** / **Proton Drive** / **Immich** | End-to-end encrypted cloud photo backup; zero server-side scanning. |
| **Fitness & Workouts** | Strava / Nike Run Club (GPS & health data harvesting) | **FitoTrack** / **Stepsy** / **openGym** | Local GPS, step counts, and gym logs without cloud transmission. |
| **Mobile Email** | Proprietary Gmail App | **Thunderbird for Android** | Connects to existing email via IMAP with zero in-app ads or Google telemetry. |
| **Core Phone Utilities** | Google / OEM Dialer, Contacts, Clock | **Fossify Suite** | Complete offline phone dialer, contacts, clock, and calculator without internet access. |

---

> [!TIP]
> **Quick Takeaway:**
> If you already deployed these FOSS tools on your mobile device, **you are finished with Level 5.** 
> **[Jump straight to Level 6: Street & FinTech Defense](06_LEVEL_SIX_STREET_AND_FINTECH_DEFENSE.md)** for real-world consumer rights and Aadhaar safety protocols. 
> *(Or scroll down to follow the individual app setup guides below.)*

---

## 1. The Gateway: F-Droid & Aurora Store 

### Step 1: Installing [F-Droid](https://f-droid.org/) (The FOSS Ecosystem)
F-Droid is an independent, community-maintained software repository for Android applications that are strictly Free and Open Source Software (FOSS).
- Every application hosted on F-Droid is compiled from audited, public source code.
- Applications with embedded tracking SDKs, advertising libraries, or anti-features are clearly flagged with warnings.
- F-Droid requires **zero account creation** and does not log download activity to an advertising profile.

### Step 2: Installing [Aurora Store](https://auroraoss.com/) (The Anonymous Play Store Bridge)
While F-Droid is the gold standard for open-source tools, Indian users still require proprietary applications that are not open-source—such as UPI banking apps (BHIM, iMobile), railway ticketing (IRCTC Rail Connect), or instant delivery apps (Zepto, Swiggy).

**The Solution:** Install **Aurora Store** (available via F-Droid or the official website).
- **Anonymous Google Tokens:** Aurora Store is an open-source client frontend for Google Play that generates a **disposable, anonymous Google session token**.
- **Zero Account Required:** You can search, download, and update genuine, un-tampered APKs straight from Google's servers without logging into your personal Google account.
- **Privacy Filter:** Aurora Store displays an Exodus Privacy tracker audit for every app *before* you install it, highlighting how many trackers and permissions are baked into the software.

---

## 2. HeliBoard: The Offline Keyboard 

Your keyboard is the single most sensitive software component on your smartphone. Every password, personal chat message, search term, and banking pin passes directly through it.

### The Problem with Gboard & SwiftKey:
Proprietary cloud keyboards utilize background network access to synchronize custom dictionaries, send predictive telemetry to corporate servers, and improve machine-learning models.

### The Solution: [HeliBoard](https://github.com/Helium314/HeliBoard) (Available on F-Droid & GitHub)
- **No Internet Permission:** HeliBoard is compiled without the Android internet permission ([`android.permission.INTERNET`](https://developer.android.com/reference/android/Manifest.permission#INTERNET)). The operating system sandbox prevents the keyboard from establishing network connections, ensuring typed text and passwords stay on-device.
- **Modern Features:** Supports swipe typing (via an offline library), multilingual dictionaries, themes, and clipboard management.
- **Indian Language Support:** Integrates offline dictionaries for regional languages with zero cloud dependency.

---

## 3. LocalSend: Clean Cross-Device File Sharing

For years, users in India relied on file-sharing tools like SHAREit or Xender, which deteriorated into ad-bloated, permission-invasive platforms repeatedly flagged for security vulnerabilities.

### The Solution: [LocalSend](https://localsend.org/) (Open-Source & Cross-Platform)
- **Local Network Only:** Transfers files, photos, and text snippets securely over your local Wi-Fi network without routing data through external cloud servers.
- **Local Network Operation:** Operates over your local Wi-Fi router or mobile hotspot without routing through external servers.
- **Universal Cross-Platform Compatibility:** Runs seamlessly across Android, Linux, Windows, macOS, and iOS—eliminating the need for proprietary vendor ecosystems.
- **End-to-End Encryption:** File transfers are encrypted using HTTPS directly between devices on your local network.

---

## 4. Distraction-Free Video Streaming: NewPipe & Brave YouTube Bypass

The official YouTube mobile app is heavily optimized for engagement loops, unskippable commercial advertisements, and continuous watch-history telemetry.

### Option A (Dedicated App): [NewPipe](https://newpipe.net/) (Available on F-Droid)
- **Zero Advertisements:** Completely blocks pre-roll, mid-roll, and banner video advertisements.
- **Background & Screen-Off Playback:** Allows background audio listening without a paid subscription.
- **Account-Free Subscriptions:** Subscribe to channels, build playlists, and bookmark videos locally on your device without logging into a Google account.
- **Lightweight Architecture:** Consumes a fraction of the RAM and storage of the official client.

### Option B (Browser Workflow): YouTube in Brave Browser
If you prefer not to install an extra app:
- Open `m.youtube.com` inside **Brave Browser**.
- Brave's built-in Shields automatically block all video ads.
- Enable **"Background Play"** in Brave's Settings (`Settings ➔ Media ➔ Background Play`) to continue listening to podcasts, music, and lectures with your screen turned off without requiring a subscription.

---

## 5. Aves Libre: Clean Offline Gallery 

Many budget and mid-range Android OEM gallery apps in India push cloud storage upsells, display banner ads, or request internet permissions.

### The Solution: [Aves Libre](https://github.com/deckerst/aves) (Available on F-Droid)
- **Complete Offline Operation:** Built strictly for local storage browsing with zero network telemetry.
- **Metadata & EXIF Inspection:** Allows you to view, inspect, and strip sensitive GPS location metadata from photos before sharing them online.
- **Fast & Responsive:** High-performance viewing across large photo and video collections with no cloud synchronization bloat.

---

## 6. Escaping Google Photos: End-to-End Encrypted Photo Backups

Google Photos is one of the most comprehensive biometric and spatial surveillance honeypots in existence: scanning faces, cataloging objects, clustering geolocations, and utilizing user images to train proprietary machine-learning models.

### Top Replacements for Secure Photo Storage:

1. **[Ente Photos](https://ente.io/) (Recommended Cloud Solution):**
 - **True End-to-End Encryption:** Photos and videos are encrypted on your device *before* uploading. Not even Ente's engineers or servers can view your files.
 - **Indian Engineering & Global Audits:** Founded and engineered in India (Kochi, Kerala) with third-party cryptographic audits by Cure53.
 - **Direct Google Photos Alternative:** Features automatic background camera backup, family albums, and desktop clients across Android, iOS, Linux, and web.

2. **[Proton Drive](https://proton.me/drive):**
 - Swiss-based encrypted cloud storage with native automated mobile camera roll uploads.
 - Integrates cleanly if you already use Proton Mail or Proton Pass.

3. **[Immich](https://immich.app/) (Self-Hosted Power User):**
 - An open-source, high-performance self-hosted backup solution for users running a home server, Raspberry Pi, or NAS.
 - Features local on-device machine-learning facial recognition and search that never transmits a single byte over the public internet.

---

## 7. Fitness & Biometric Autonomy: Decoupling Workouts from the Cloud

Commercial fitness and running applications (such as **Strava**, **Nike Run Club**, **Google Fit**, **Zepp Life / Mi Fitness**, and **Cult.fit**) operate as aggressive spatial and biometric surveillance networks.

### The Problem with Cloud Fitness Trackers:
- **Continuous High-Precision GPS Harvesting:** Commercial running apps log your exact running routes, pace, residential departure times, and destination coordinates. In 2018, Strava's public heatmap famously exposed the exact layouts and patrol routes of military installations worldwide—proving how granular and persistent this location harvesting is.
- **Biometric Commercialization:** Heart rates, daily step counts, calorie burn, and weight metrics are synchronized to corporate servers, monetized through advertising networks, or packaged for actuarial analysis by health insurance brokers.
- **The Core Sovereignty Principle:** *Your physical training data does not need to live on someone else's cloud server.*

---

### The Sovereign FOSS Fitness Stack:

#### 1. Outdoor Running & Cycling: [FitoTrack](https://f-droid.org/packages/de.tadris.fitness/) (Available on F-Droid & Play Store)
- **Offline by Design (GPLv3):** FitoTrack is an open-source fitness tracker that logs running, cycling, hiking, and walking sessions without ads, accounts, or cloud dependencies.
- **Local Route Logging:** Records your GPS route, speed, pace, elevation, and calories purely to local device storage.
- **Local Bluetooth Sensor Support:** Connects directly to standard Bluetooth Low Energy (BLE) heart-rate chest straps and cadence sensors without requiring proprietary manufacturer cloud accounts.
- **Data Portability:** Exports your workout data directly to standard `.gpx` files on your phone, allowing you to back up or analyze your workouts without corporate vendor lock-in.

#### 2. Daily Step Counting: [Stepsy](https://f-droid.org/) (Available on F-Droid / GitHub)
- **Zero Battery Drain & Zero Trackers:** Stepsy uses your phone's built-in hardware step sensor to record daily walking metrics without keeping your GPS radio active.
- **Offline Operation:** Operates without requiring network connectivity, account registration, or background analytics.
- **Local Insights:** Displays clean daily and weekly step trends and streaks directly on your device.

#### 3. Strength Training & Gym Workouts: [openGym](https://github.com/DuarteSantos8/openGym) / [wger](https://wger.de/)
- **Workout Logging Without Commercial Subscriptions:** Track weightlifting routines, sets, reps, body weight, and workout history without paying monthly subscription fees or sitting through sponsored fitness influencer feeds.
- **Self-Hosted Autonomy:** If you want cross-device syncing between your phone and computer, open-source solutions like `openGym` or `wger` allow you to sync against your own private server using modern passkeys, maintaining complete ownership over your physical progression.

---

## 8. Replacing Default OEM Apps: The Fossify Suite

Most pre-installed system apps on Android—including Google Phone (Dialer), Google Contacts, and OEM Clock or Calculator utilities—require internet access and transmit device analytics. In many OEM skins (Xiaomi, Realme, Vivo), basic utility apps display inline recommendations or advertisements.

### The Solution: The [Fossify Suite](https://github.com/FossifyOrg) (Available on F-Droid)
Fossify is the clean, community-led open-source fork of the acclaimed Simple Mobile Tools ecosystem (created after the original project was acquired by an advertising vendor):

1. **[Fossify Phone & Contacts](https://github.com/FossifyOrg/Phone):** A clean offline dialer and contact manager. Your address book stays stored exclusively on your device rather than syncing contacts to Google's cloud servers.
2. **[Fossify Clock](https://github.com/FossifyOrg/Clock) & [Fossify Calculator](https://github.com/FossifyOrg/Calculator):** Fast, utility-focused tools compiled **without the internet permission (`android.permission.INTERNET`)**. They execute calculations and alarms locally without network permissions.
3. **[Fossify Calendar](https://github.com/FossifyOrg/Calendar):** Manages offline schedules and events without syncing your personal itinerary to corporate cloud calendars.
4. **[Thunderbird for Android](https://www.thunderbird.net/) (Email Client):** The open-source standard (built on K-9 Mail) to replace the pre-installed Gmail app. Manages your existing email accounts over standard IMAP/SMTP without commercial tracking modules and strips embedded tracking pixels.

---

## 9. The "Under-The-Hood" Illusion: Neutralizing System Shadow Daemons

A widespread misconception among privacy-conscious smartphone users is: *"I installed F-Droid, HeliBoard, Fossify Messages, and Aves Libre. My phone is now private."*

This is a dangerous half-truth. On standard stock Android, merely installing FOSS alternatives does **not** stop the pre-installed Google, Qualcomm, and OEM system daemons from harvesting data below user space.

> [!NOTE]
> **Real-World Hardware Case Study:**  
> This empirical investigation was audited directly on a **Nothing Phone (Nothing OS / A059 series)**. While other manufacturers (Xiaomi/POCO, Samsung, OnePlus, Realme, Vivo) bundle their own brand-specific bloatware suites, this case study exposes the universal tracking architecture that operates under the hood across modern consumer Android smartphones.

---

### The Five "Under-The-Hood" Surveillance Leaks:

#### 1. The Shared System Database Trap (Contacts & Photos)
In Android, contacts and media live in centralized OS provider databases (`ContactsContract` and `MediaStore`). 
* Even if you only open **Fossify Contacts**, the moment you save a new contact, it is written to the central database. Stock **Google Contacts** wakes up via background system listeners and automatically syncs that new phone number and name directly to Google's cloud servers (`contacts.google.com`).
* Even if you view photos exclusively in **Aves Libre**, stock **Google Photos** registers background system jobs that parse the **EXIF metadata (your exact GPS coordinates and timestamps)** of every newly captured photo.
* **The Fix:** Completely uninstall the stock Google Contacts and Google Photos packages from your user profile.

#### 2. The SMS OTP Interception Backdoor (`SmsRetriever` API)
If you have ever entered an OTP on a shopping or banking app and suddenly seen a Google Play banner pop up asking to *"Autofill / Copy code"*, you witnessed this backdoor in action.
* Even when **Fossify Messages** is your default SMS app, shopping and fintech apps call the **Google Play Services SDK** (`com.google.android.gms.auth.api.phone.SmsRetriever`).
* Because Google Play Services operates with privileged system status (`priv-app`), it intercepts inbound cellular SMS broadcasts at the OS layer alongside your SMS app—logging the merchant, timestamp, and transaction context before you even open your message.
* **The In-Device Fix:** Go to **Settings → Google (All Services) → Autofill with Google → SMS verification codes → Toggle OFF**.

#### 3. The `SYSTEM_FIXED` OEM Betrayal (Call Logs & Location)
When auditing Nothing OS, we inspected the internal permissions granted to the background daemon `com.nothing.experience`. Its package manifest revealed:
```text
android.permission.READ_CALL_LOG: granted=true, flags=[SYSTEM_FIXED]
android.permission.ACCESS_FINE_LOCATION: granted=true, flags=[SYSTEM_FIXED]
```
The OEM hardcoded permanent, non-revocable system permissions allowing this background daemon to log **who you call, how long you speak, and your exact latitude and longitude at that precise second**. Because it was flagged as `SYSTEM_FIXED`, the standard Android Settings UI hid the permission toggle from the user.

#### 4. The 24/7 Always-On Microphone Listeners
Background packages `com.android.hotwordenrollment.okgoogle`, `com.android.hotwordenrollment.xgoogle`, and Qualcomm chipset daemons (`com.qualcomm.qti.voiceai.speech`) keep the low-power Digital Signal Processor (DSP) microphone buffer powered on 24/7, continuously analyzing ambient room frequencies for acoustic trigger patterns.

#### 5. The OS-Level Ad Profiler (Privacy Sandbox & Digital Wellbeing)
Under the guise of a productivity tool, **Digital Wellbeing** (`com.google.android.apps.wellbeing`) creates an exact, timestamped ledger of your life: the precise second you unlock your phone at night, and how many seconds you spend on your banking or messaging apps. Paired with Google's modular **Mainline AdServices** (`com.google.mainline.adservices`), the operating system itself computes your commercial demographic profile and exposes an on-device API for advertisers.

---

### The Safe Neutralization Blueprint (Non-Root / Bootloader Locked)

You do **not** need to root your phone or unlock your bootloader (which would break banking apps and Google Play Integrity). Using standard ADB commands over USB from your computer, you can disable and neutralize these daemons for your primary user profile (`--user 0`):

```bash
# -------------------------------------------------------------
# 1. Kill Redundant Stock Apps (You have FOSS replacements)
# -------------------------------------------------------------
adb shell pm uninstall -k --user 0 com.google.android.inputmethod.latin   # Gboard (Replaced by HeliBoard)
adb shell pm uninstall -k --user 0 com.google.android.contacts           # Google Contacts (Replaced by Fossify)
adb shell pm uninstall -k --user 0 com.google.android.apps.messaging     # Google Messages (Replaced by Fossify)
adb shell pm uninstall -k --user 0 com.google.android.apps.photos        # Google Photos (Replaced by Aves Libre)
adb shell pm uninstall -k --user 0 com.google.android.apps.docs          # Google Docs (Replaced by OnlyOffice)

# -------------------------------------------------------------
# 2. Kill Always-On Microphone Listeners
# -------------------------------------------------------------
adb shell pm uninstall -k --user 0 com.android.hotwordenrollment.okgoogle
adb shell pm uninstall -k --user 0 com.android.hotwordenrollment.xgoogle
adb shell pm uninstall -k --user 0 com.qualcomm.qti.voiceai.speech

# -------------------------------------------------------------
# 3. Kill OS-Level Ad Engines & Behavioral Loggers
# -------------------------------------------------------------
adb shell pm uninstall -k --user 0 com.google.mainline.adservices
adb shell pm uninstall -k --user 0 com.google.mainline.telemetry
adb shell pm uninstall -k --user 0 com.google.android.adservices.api
adb shell pm uninstall -k --user 0 com.google.android.apps.wellbeing
adb shell pm uninstall -k --user 0 com.google.android.ondevicepersonalization.services
adb shell pm uninstall -k --user 0 com.google.android.federatedcompute
adb shell pm uninstall -k --user 0 com.google.android.apps.bard          # Gemini Background Agent
adb shell pm uninstall -k --user 0 com.google.android.feedback
adb shell pm uninstall -k --user 0 com.google.android.partnersetup

# -------------------------------------------------------------
# 4. Freeze Hardcoded OEM Telemetry (For protected packages)
# -------------------------------------------------------------
# Packages returning [DELETE_FAILED_INTERNAL_ERROR] must be disabled:
adb shell pm disable-user --user 0 com.nothing.experience
adb shell pm disable-user --user 0 com.nothing.logkit
adb shell pm disable-user --user 0 com.nothing.appservice                 # Silent partner app installer
adb shell pm disable-user --user 0 com.nothing.essentialintelligence      # AI behavior tracking engine
adb shell pm disable-user --user 0 com.nothing.aiwidget
adb shell pm disable-user --user 0 com.nothing.user.center
adb shell pm disable-user --user 0 com.nothing.universal.search           # Search indexing
adb shell pm disable-user --user 0 com.nothing.ntessentialspace           # Dedicated Essential Button service
adb shell pm disable-user --user 0 com.nothing.ntessentialrecorder        # Essential Voice recorder
adb shell pm disable-user --user 0 com.nothing.ntgamedashboard
adb shell pm disable-user --user 0 com.nothing.userguide
adb shell pm disable-user --user 0 com.nothing.introduction16

# Enforce Kernel-Level AppOps Restrictions:
adb shell cmd appops set com.nothing.experience RUN_IN_BACKGROUND ignore
adb shell cmd appops set com.nothing.experience RUN_ANY_IN_BACKGROUND ignore
adb shell cmd appops set com.nothing.experience READ_SMS ignore
adb shell cmd appops set com.nothing.experience BODY_SENSORS ignore

# -------------------------------------------------------------
# 5. Kill Hardware Statistics, Promoted Installs & AI Loggers
# -------------------------------------------------------------
adb shell pm uninstall -k --user 0 com.qualcomm.qti.devicestatisticsservice
adb shell pm disable-user --user 0 com.tools.cit
adb shell pm uninstall -k --user 0 android.autoinstalls.config.Nothing
adb shell pm uninstall -k --user 0 android.autoinstalls.config.Xiaomi.model
adb shell pm uninstall -k --user 0 com.google.android.apps.turbo          # Device Health Services telemetry
adb shell pm uninstall -k --user 0 com.google.android.as                 # Android System Intelligence telemetry
adb shell pm uninstall -k --user 0 com.google.android.as.oss
adb shell pm uninstall -k --user 0 com.google.android.gms.location.history
adb shell pm uninstall -k --user 0 com.google.android.gms.supervision
adb shell pm uninstall -k --user 0 com.google.android.apps.work.clouddpc  # Enterprise/MDM cloud telemetry
adb shell pm uninstall -k --user 0 com.google.android.contactkeys
adb shell pm uninstall -k --user 0 com.google.android.apps.restore        # Cloud sync/restore daemon
adb shell pm uninstall -k --user 0 com.google.android.apps.safetyhub      # Safety tracking daemon
adb shell pm uninstall -k --user 0 com.google.android.apps.carrier.carrierwifi

# -------------------------------------------------------------
# 6. Contain Google Play Services (GMS) via Kernel-Level AppOps Sandbox
# -------------------------------------------------------------
# DO NOT uninstall Google Play Services (GMS) directly on daily devices,
# as complete removal breaks banking apps, UPI, and Firebase Cloud Messaging (FCM).
# Instead, sandbox GMS at the kernel/Binder level using AppOps. This forces GMS
# to return empty/mock null responses to surveillance queries while preserving 
# 100% working push notifications, Play Integrity attestation, and biometrics.

# Silence SMS Sniffing & OTP Interception:
adb shell cmd appops set com.google.android.gms RECEIVE_SMS ignore
adb shell cmd appops set com.google.android.gms READ_SMS ignore
adb shell cmd appops set com.google.android.gms SEND_SMS ignore
adb shell cmd appops set com.google.android.gms WRITE_SMS ignore
adb shell pm revoke com.google.android.gms android.permission.RECEIVE_SMS 2>/dev/null
adb shell pm revoke com.google.android.gms android.permission.READ_SMS 2>/dev/null

# Block Calls, Contacts & Call Log Surveillance:
adb shell cmd appops set com.google.android.gms READ_CONTACTS ignore
adb shell cmd appops set com.google.android.gms WRITE_CONTACTS ignore
adb shell cmd appops set com.google.android.gms READ_CALL_LOG ignore
adb shell cmd appops set com.google.android.gms PROCESS_OUTGOING_CALLS ignore

# Block Physical Location & Motion/Activity Profiling:
adb shell cmd appops set com.google.android.gms COARSE_LOCATION ignore
adb shell cmd appops set com.google.android.gms FINE_LOCATION ignore
adb shell cmd appops set com.google.android.gms GPS ignore
adb shell cmd appops set com.google.android.gms MONITOR_LOCATION ignore
adb shell cmd appops set com.google.android.gms MONITOR_HIGH_POWER_LOCATION ignore
adb shell cmd appops set com.google.android.gms ACTIVITY_RECOGNITION ignore
adb shell cmd appops set com.google.android.gms BODY_SENSORS ignore

# Block Microphone, Camera & Gallery Snooping:
adb shell cmd appops set com.google.android.gms RECORD_AUDIO ignore
adb shell cmd appops set com.google.android.gms CAMERA ignore
adb shell cmd appops set com.google.android.gms READ_MEDIA_IMAGES ignore
adb shell cmd appops set com.google.android.gms READ_MEDIA_VIDEO ignore
adb shell cmd appops set com.google.android.gms READ_MEDIA_AUDIO ignore
adb shell cmd appops set com.google.android.gms READ_EXTERNAL_STORAGE ignore
adb shell cmd appops set com.google.android.gms WRITE_EXTERNAL_STORAGE ignore

# Block Wireless Beacons & Clipboard Snooping (GMS & Play Store):
adb shell cmd appops set com.google.android.gms BLUETOOTH_SCAN ignore
adb shell cmd appops set com.google.android.gms BLUETOOTH_CONNECT ignore
adb shell cmd appops set com.google.android.gms BLUETOOTH_ADVERTISE ignore
adb shell cmd appops set com.google.android.gms NEARBY_WIFI_DEVICES ignore
adb shell cmd appops set com.google.android.gms WIFI_SCAN ignore
adb shell cmd appops set com.google.android.gms READ_CLIPBOARD ignore
adb shell cmd appops set com.android.vending READ_CLIPBOARD ignore
adb shell cmd appops set com.android.vending COARSE_LOCATION ignore
adb shell cmd appops set com.android.vending FINE_LOCATION ignore
```

> [!TIP]
> **Detailed Forensic Case Study:**  
> For the complete, unredacted forensic timeline showing live ADB timestamps of Google Play Services intercepting financial OTPs, Outgoing Calls, and exploiting DualApps profiles, read the companion case study:  
> **[Forensic Case Study: Defanging Surveillance Capitalism on Nothing Phone (2a)](../case_studies/NOTHING_PHONE_2A_FORENSIC_DEBLOAT_CASE_STUDY.md)**.

> [!CAUTION]
> ### OEM Bootloop Tripwires: What NEVER to Uninstall
> 1. **Android 14, 15 & 16 (`com.google.android.sdksandbox`):**
>    Android's core `PackageManagerService.java` hardcodes a dependency on `com.google.android.sdksandbox` via `getRequiredSdkSandboxPackageName()`. **Never** uninstall or disable this package for user 0, or `system_server` will crash endlessly on boot.
> 2. **Xiaomi MIUI / HyperOS (`com.xiaomi.finddevice`):**
>    Xiaomi's proprietary `SecurityManagerService.java` enforces a hardcoded signature check on boot (`connot find system app : com.xiaomi.finddevice`). Uninstalling it causes an immediate boot-loop on the Mi splash screen. **Do not uninstall `com.xiaomi.finddevice`**; instead, castrate its permissions via AppOps (`cmd appops set com.xiaomi.finddevice <OP> ignore`) and revoke its location permissions while leaving the inert package registered.

---

### What Happens During Software Updates?
* **Monthly Security Patches:** Do **not** restore these packages. Android preserves user package restrictions across minor security updates.
* **Major OS Upgrades (e.g., Android 14 → 15):** The OEM may re-provision default system packages. If this occurs, simply reconnect your phone to your computer and re-run the script above—it takes less than 10 seconds to re-silence the entire apparatus.

---

## Technical Boundaries & Limitations of Level 5

* **ADB Package Removal (`--user 0`) vs. System Image Partitioning:** Running `pm uninstall -k --user 0` removes the package from the primary user space (user 0), stopping execution, background services, and storage access. However, because stock Android system partitions (`/system`, `/product`, `/system_ext`) are mounted read-only (`dm-verity`), the underlying APK files remain in storage and can be re-provisioned if a factory reset occurs or after major OS version upgrades (e.g., Android 14 to 15).
* **FCM Push Notifications vs. Google Play Services:** FOSS apps downloaded from F-Droid (like Thunderbird or Signal) implement their own background polling or persistent websockets. However, many proprietary third-party apps (banking, food delivery, ride-hailing) rely exclusively on Google Cloud Messaging / Firebase Cloud Messaging (FCM). Completely uninstalling Google Play Services breaks push notifications for these apps unless running on an OS with sandboxed Google Play (like GrapheneOS) or microG.
* **Banking / UPI Attestation (Play Integrity / SafetyNet):** Replacing stock dialers, keyboards, and browsers with FOSS apps does not affect UPI apps (BHIM, PhonePe, Google Pay). However, attempting to root your phone or unlock the bootloader to physically delete system APKs trips Android's hardware-backed Play Integrity API (`MEETS_DEVICE_INTEGRITY`), which breaks banking and UPI authentication. Non-root ADB debloating as documented maintains hardware-backed Play Integrity (`MEETS_DEVICE_INTEGRITY`) attestation.

---

## Completed Checklist

- [x] F-Droid installed as an independent open-source application portal.
- [x] Aurora Store configured for anonymous Play Store access without personal Gmail linking.
- [x] HeliBoard set as the default system keyboard with zero internet permissions.
- [x] LocalSend installed across mobile and desktop devices for secure local file sharing.
- [x] NewPipe deployed or Brave Background Play enabled for clean, ad-free video streaming.
- [x] Aves Libre active for private, offline photo and video management.
- [x] Cloud photo backup transitioned away from Google Photos to an end-to-end encrypted vault (Ente / Proton / Immich).
- [x] Fitness and workout tracking decoupled from corporate clouds via offline tools (FitoTrack, Stepsy, openGym).
- [x] Basic OEM utilities (dialer, contacts, clock, calculator) replaced with telemetry-free Fossify tools.
- [x] Mobile email transitioned away from the stock Gmail app to Thunderbird for Android or an encrypted client.
- [x] Google SMS Verification Code autofill interception disabled in Google system settings.
- [x] Redundant stock Google syncers (Gboard, Contacts, Messages, Photos) uninstalled via ADB.
- [x] Always-on microphone hotwords and Qualcomm Voice-AI listeners neutralized.
- [x] OS-level ad engines (Mainline AdServices, Wellbeing logger, Federated Compute) uninstalled.
- [x] Hardcoded OEM telemetry daemons frozen (`disabled-user`) with background AppOps restrictions enforced.

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your device:

1. **Local Keystroke Processing:** Your keyboard processes text locally without network permissions. Keystroke patterns, personal chats, and search entries cannot be uploaded to remote cloud services.
2. **Anonymous App Acquisitions:** You download necessary proprietary Android applications via Aurora Store without associating your device installations with a personal Google advertising ID.
3. **Local, Ad-Free File Transfer:** Moving files between your phone, laptop, or other devices occurs over local Wi-Fi with end-to-end encryption—bypassing proprietary cloud bridges.
4. **Distraction-Free Video Streaming:** Video content plays without unskippable commercial ads, algorithmic watch-history profiling, or mandatory account logins.
5. **Metadata Sovereignty:** You have full visibility over photo EXIF metadata and GPS tags before images leave your device.
6. **Biometric Photo Isolation:** Your personal photos and family albums are end-to-end encrypted, preventing automated facial recognition, spatial indexing, or commercial AI training.
7. **Biometric & Route Autonomy:** Your daily step counts, running routes, and gym workouts are logged locally on-device. No fitness corporation, insurer, or social feed monitors your physical movement or coordinates.
8. **Sanitized Core Utilities:** Your dialer, address book, clock, and calculator operate strictly offline with zero call-log telemetry or cloud synchronization.

---
**Support the Project:** Star this repository on GitHub to help other Indian developers, students, and citizens discover it.
> **Reporting Changed Packages or Inaccuracies:**  
> If an OEM update has altered package names or introduced new system daemons on your device model, please [open an issue on GitHub](https://github.com/rack0911/digital-swaraj/issues) with your package audit list.

---
**Proceed to [Level 6: Street & FinTech Defense](06_LEVEL_SIX_STREET_AND_FINTECH_DEFENSE.md)**
