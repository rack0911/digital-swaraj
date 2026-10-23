# Level 5: The Mobile FOSS Stack (Clean Open-Source Replacements)

> ###  Time Required: 15 Minutes | Difficulty: Intermediate | Workflow Disruption: Low
> 
> *The average smartphone in India comes pre-loaded with proprietary utilities: keyboards that transmit keystroke telemetry to cloud servers, gallery apps with full-screen banner ads, dialers that sync call logs, and file-sharing utilities riddled with bloatware. In Level 5, we replace these daily tools with clean, lightweight Free and Open Source Software (FOSS) that respects your privacy and contains zero advertising.*

---

## The 60-Second Action Plan

| Vector | Bloated Proprietary Default | The FOSS Replacement | Direct Result |
| :--- | :--- | :--- | :--- |
| **App Store (FOSS)** | Google Play Store (exclusively) | **F-Droid** | Access verified, tracking-free open-source mobile software. |
| **App Store (Proprietary)** | Google Play logged into personal Gmail | **Aurora Store** | Anonymous Play Store client; downloads genuine APKs without a Google account. |
| **Keyboard** | Gboard / SwiftKey | **HeliBoard** | 100% offline typing; zero keystroke telemetry or cloud sync. |
| **Local File Share** | SHAREit / Quick Share / Nearby | **LocalSend** | Encrypted peer-to-peer file transfer over local Wi-Fi across Android, PC, and iOS. |
| **Video Streaming** | YouTube App (heavy ads & tracking) | **NewPipe** or **Brave Browser** | Ad-free viewing, background audio playback, zero Google account required. |
| **Photo Gallery** | Proprietary OEM Gallery with ads | **Aves Libre** | Fast, clean, offline media management with full metadata and EXIF control. |
| **Cloud Photo Backup** | Google Photos (facial recognition & indexing) | **Ente Photos** / **Proton Drive** / **Immich** | End-to-end encrypted cloud photo backup; zero server-side scanning. |
| **Fitness & Workouts** | Strava / Nike Run Club (GPS & health data harvesting) | **FitoTrack** / **Stepsy** / **openGym** | 100% offline running GPS, step counts, and gym logs; zero cloud telemetry. |
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
- **Zero Internet Permission:** HeliBoard is compiled **without the Android Internet permission (`android.permission.INTERNET`)**. It is physically impossible for the app to transmit a single byte of data off your phone.
- **Modern Features:** Supports swipe typing (via an offline library), multilingual dictionaries, themes, and clipboard management.
- **Indian Language Support:** Integrates offline dictionaries for regional languages with zero cloud dependency.

---

## 3. LocalSend: Clean Cross-Device File Sharing

For years, users in India relied on file-sharing tools like SHAREit or Xender, which deteriorated into ad-bloated, permission-invasive platforms repeatedly flagged for security vulnerabilities.

### The Solution: [LocalSend](https://localsend.org/) (Open-Source & Cross-Platform)
- **Local Network Only:** Transfers files, photos, and text snippets securely over your local Wi-Fi network without routing data through external cloud servers.
- **Zero Internet Required:** Works completely offline using a local Wi-Fi router or mobile hotspot.
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
- Enable **"Background Play"** in Brave's Settings (`Settings ➔ Media ➔ Background Play`) to continue listening to podcasts, music, and lectures with your screen turned off—100% free without YouTube Premium.

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
- **100% Offline & Open-Source (GPLv3):** FitoTrack is a dedicated fitness tracker that logs running, cycling, hiking, and walking sessions without ads, accounts, or cloud dependencies.
- **Local Route Logging:** Records your GPS route, speed, pace, elevation, and calories purely to local device storage.
- **Local Bluetooth Sensor Support:** Connects directly to standard Bluetooth Low Energy (BLE) heart-rate chest straps and cadence sensors without requiring proprietary manufacturer cloud accounts.
- **Data Portability:** Exports your workout data directly to standard `.gpx` files on your phone, allowing you to back up or analyze your workouts without corporate vendor lock-in.

#### 2. Daily Step Counting: [Stepsy](https://f-droid.org/) (Available on F-Droid / GitHub)
- **Zero Battery Drain & Zero Trackers:** Stepsy uses your phone's built-in hardware step sensor to record daily walking metrics without keeping your GPS radio active.
- **100% Offline Operation:** Operates without an internet connection, account registration, or background analytics.
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
2. **[Fossify Clock](https://github.com/FossifyOrg/Clock) & [Fossify Calculator](https://github.com/FossifyOrg/Calculator):** Fast, utility-focused tools compiled **without the internet permission (`android.permission.INTERNET`)**. They execute calculations and alarms locally with zero telemetry.
3. **[Fossify Calendar](https://github.com/FossifyOrg/Calendar):** Manages offline schedules and events without syncing your personal itinerary to corporate cloud calendars.
4. **[Thunderbird for Android](https://www.thunderbird.net/) (Email Client):** The open-source standard (built on K-9 Mail) to replace the pre-installed Gmail app. Manages your existing email accounts over standard IMAP/SMTP with zero telemetry and automatic email spy pixel stripping.

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

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your device:

1. **Zero Keystroke Telemetry:** Your keyboard hardware transcribes text completely offline. No typing patterns, personal messages, or search entries can be transmitted to cloud servers.
2. **Anonymous App Acquisitions:** You download necessary proprietary Android applications via Aurora Store without associating your device installations with a personal Google advertising ID.
3. **Local, Ad-Free File Transfer:** Moving files between your phone, laptop, or other devices occurs over local Wi-Fi with end-to-end encryption—bypassing proprietary cloud bridges.
4. **Distraction-Free Video Streaming:** Video content plays without unskippable commercial ads, algorithmic watch-history profiling, or mandatory account logins.
5. **Metadata Sovereignty:** You have full visibility over photo EXIF metadata and GPS tags before images leave your device.
6. **Biometric Photo Isolation:** Your personal photos and family albums are end-to-end encrypted, preventing automated facial recognition, spatial indexing, or commercial AI training.
7. **Biometric & Route Autonomy:** Your daily step counts, running routes, and gym workouts are logged 100% on-device. No fitness corporation, insurer, or social feed monitors your physical movement or coordinates.
8. **Sanitized Core Utilities:** Your dialer, address book, clock, and calculator operate strictly offline with zero call-log telemetry or cloud synchronization.

---
**Support the Project:** Star this repository on GitHub to help other Indian developers, students, and citizens discover it.
**Proceed to [Level 6: Street & FinTech Defense](06_LEVEL_SIX_STREET_AND_FINTECH_DEFENSE.md)**
