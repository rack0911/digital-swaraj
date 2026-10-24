# Level 0: The Default Trap (What They Know While You Sleep)

> **Document Status:** Verified (Current as of October 2026)  
> **Supported Scope:** Android 12, 13, 14, 15; CCPA Dark Patterns Guidelines (2023); RBI Digital Lending Directions (2022); UIDAI Regulations  
> **Official Primary Citations:** [MoCA Advisory (PIB PRID 1926639)](https://pib.gov.in/PressReleasePage.aspx?PRID=1926639), [CCPA Dark Patterns Notification (2023)](https://consumeraffairs.nic.in/sites/default/files/CCPA_Notification.pdf), [RBI Digital Lending Directions](https://www.rbi.org.in/Scripts/BS_CircularIndexDisplay.aspx?Id=12382), [Puttaswamy Right to Privacy Judgment (2017)](https://main.sci.gov.in/supremecourt/2012/35071/35071_2012_Judgement_24-Aug-2017.pdf)

---

> ### Public Interest & Legal Notice
> This document is published strictly for educational and consumer awareness under **Article 19(1)(a)** and **Article 21 (Right to Privacy)** of the Constitution of India (*Justice K.S. Puttaswamy (Retd.) v. Union of India*, 2017). All observations reference documented system defaults, official advisories from the **Ministry of Consumer Affairs**, the **CCPA Guidelines for Prevention of Dark Patterns (2023)**, **RBI Digital Lending Guidelines**, and **CERT-In**. All product names are used solely for descriptive, nominative identification under **Section 30 of the Trade Marks Act, 1999**.

---

> *"I have nothing to hide. Why would tech companies care about an average person like me?"* 
> — Every smartphone user before inspecting what default settings broadcast 24/7.

---

## The 60-Second Reality Check

| Everyday Indian Habit | What We Assume | What Actually Happens |
| :--- | :--- | :--- |
| **Xerox / Print Shop** | *"Just a quick ₹10 printout."* | Clean Aadhaar/PAN PDF left permanently in a public PC's `Downloads` folder. |
| **₹15 Tea Stall via UPI** | *"Just transferring money."* | High-accuracy GPS coords logged into your commercial profile to verify daily routines. |
| **Retail Counter Phone Number** | *"System requires it for bill."* | Cashier pressured to capture your universal tracking key (prohibited by Consumer Affairs). |
| **Loyalty Points at Checkout** | *"Saving ₹5 on next visit."* | Trading your entire lifetime shopping basket history for 50 expiring reward points. |
| **Festive Lucky Draw Box** | *"Entering to win a car."* | Handing your full name, mobile, and home address to unregulated real-estate lead brokers. |
| **9:15 AM Market Alerts** | *"Helpful financial update."* | Commercial entities using WhatsApp Business API to bypass DND and provoke panic trades. |
| **Caller-ID Directory Apps** | *"I never installed them."* | Your contacts uploaded by friends/relatives, indexing your private number into public databases. |
| **Flashlight / Ludo Permissions** | *"Standard Android popups."* | Casual games accessing Call Logs & SMS to scrape bank balances (flagged by RBI/CERT-In). |
| **Discarded Delivery Box** | *"Just useless cardboard."* | Thermal shipping stickers in garbage chutes harvested for verified residential contact lists. |
| **Toggling Wi-Fi / Bluetooth 'Off'** | *"Radios are silent."* | Background Wi-Fi & Bluetooth probe scanning remains active 24/7 in system settings. |
| **Gmail Receipt Inbox** | *"Private personal email."* | Public dashboard was quietly killed after backlash, but automated receipt scanning continues via Smart Features. |

---

> [!TIP]
> **Quick Takeaway:**
> If this 60-second table gave you the picture, **you do not need to spend time reading further.** 
> **[Jump straight to Level 1: The Zero-Effort Shield](01_LEVEL_ONE_BROWSER_AND_DNS.md)** to start locking down your setup in under 10 minutes. 
> *(Or scroll down if you want the quick 3-bullet breakdown of each trap below.)*

---

## The 10 Traps: Street-Level Breakdowns

### 1. "Send It on WhatsApp": The Local Print Shop Dump
- **The Habit:** You walk into a photocopy shop and WhatsApp your unmasked Aadhaar or PAN card PDF to the shopkeeper's phone for an urgent printout.
- **The Extraction:** The PDF remains saved permanently in the shop's public desktop `Downloads` folder alongside hundreds of other customer IDs, salary slips, and bank statements.
- **The Risk:** Anyone with a USB drive can copy thousands of high-resolution identity documents in under a minute—feeding the exact pipeline warned about by **CERT-In** (unauthorized SIM registrations and predatory micro-loans).

### 2. The ₹15 Street Tea Stall & The GPS Location Lock
- **The Habit:** You scan a vendor's UPI QR code with battery at 15% and GPS toggled off; the app refuses to proceed until you enable device location.
- **The Extraction:** Third-Party App Providers (TPAPs) log high-precision satellite coordinates, timestamps, and spending patterns under omnibus Privacy Policies.
- **The Risk:** Your physical routine, commute schedule, and disposable cash flow are profiled—triggering targeted loan and credit offers precisely when your monthly balance dips.

### 3. The Retail Checkout Interrogation & Loyalty Points 
- **The Habit:** Cashiers at clothing chains or supermarkets claim *"the billing system cannot generate an invoice without your mobile number"*, or offer 50 loyalty points.
- **The Extraction:** Your 10-digit number acts as a universal identifier linking your offline purchases to online ad profiles, data brokers, and telemarketing registries.
- **The Reality:** On May 23, 2023, the Ministry of Consumer Affairs issued an explicit advisory ([PIB Press Release PRID 1926639](https://pib.gov.in/PressReleasePage.aspx?PRID=1926639)): *Retailers are legally prohibited from insisting on a consumer's mobile number as a mandatory pre-condition for generating a tax invoice.*

### 4. The Festive Lucky Draw: The Acrylic Box of Free Leads 
- **The Habit:** Outside jewelry showrooms, textile stores, or fuel stations during festival seasons, shoppers drop handwritten coupons into a box to win a car or gold coin.
- **The Extraction:** You write your full legal name, mobile number, complete residential address, and vehicle model on a paper slip dropped into an unguarded box.
- **The Risk:** One person wins a kitchen appliance; the other 50,000 slips are sold to local real estate builders and telemarketers for ₹1 to ₹3 per lead.

### 5. The 9:15 AM WhatsApp Alert: Manufactured Financial Urgency
- **The Habit:** You wake up to an urgent WhatsApp alert from an investing or trading service: *"Market down 5%! Check your portfolio impact now."*
- **The Extraction:** Because TRAI DND regulations cracked down on SMS spam, commercial entities license the WhatsApp Business API to bypass telecom filters.
- **The Reality:** Under the **Central Consumer Protection Authority (CCPA)** [Guidelines for Prevention and Regulation of Dark Patterns, 2023](https://consumeraffairs.nic.in/sites/default/files/CCPA_Notification.pdf), manufacturing artificial urgency or deploying 'False Urgency' to coerce consumer action is classified as a prohibited unfair practice.

### 6. The Collective Privacy Trap: Crowdsourced Phone Directories
- **The Habit:** You deliberately avoid installing caller-ID directory apps to protect your privacy.
- **The Extraction:** A colleague, cousin, or building security guard installs the app and taps *"Allow Contacts"*, uploading their entire address book to cloud servers.
- **The Risk:** Your private number, emergency contacts, and social labels (*"Rahul College"*, *"Rahul Colleague"*) are publicly indexed without your knowledge or consent.

### 7. The "Allow, Allow" Reflex: Why Does a Torch App Need Call Logs?
- **The Habit:** Installing a basic flashlight tool, offline Ludo game, or daily horoscope app and tapping "Allow" on every permission prompt to skip past the setup.
- **The Extraction:** Casual utilities gain access to your Full Call Logs, Contacts, SMS Inbox (`READ_SMS`), and Notification Listener services.
- **The Risk:** Background scripts parse banking SMS (`SBIINB`, `HDFCBK`) to estimate your monthly income and credit limits. Under the [RBI Guidelines on Digital Lending (RBI/2022-23/111)](https://www.rbi.org.in/Scripts/BS_CircularIndexDisplay.aspx?Id=12382), regulated entities and their digital lending apps are expressly prohibited from accessing mobile device resources such as phone contacts, call logs, and external storage.

### 8. Discarded Packaging in Apartment Waste Bins
- **The Habit:** Unpacking e-commerce parcels and throwing the cardboard boxes straight into communal corridor dustbins or waste chutes.
- **The Extraction:** Thermal shipping labels display your full legal name, phone number, complete apartment address, and order category in plain text.
- **The Risk:** Physical data harvesters and local lead generators routinely sift residential waste to compile verified high-income neighbourhood contact directories.

### 9. Phantom Radios: Background Scanning When Radios Are "Off"
- **The Habit:** Toggling Wi-Fi and Bluetooth to "Off" in your phone's quick-settings panel and assuming your device is invisible.
- **The Extraction:** Under `Settings ➔ Location ➔ Location Services`, Android operating systems maintain background radio polling via [`WifiManager.isScanAlwaysAvailable()`](https://developer.android.com/reference/android/net/wifi/WifiManager#isScanAlwaysAvailable()) and BLE background scanners, even when user-facing toggles in Quick Settings are turned off.
- **The Risk:** In addition to transmitting probe request frames, scanning continuously harvests the BSSIDs of nearby Wi-Fi routers to feed crowdsourced location databases (like Google Location Accuracy) without requiring satellite GPS.

### 10. The Hidden Purchases Dashboard & Active Email Parsing
- **The Habit:** Assuming your commercial receipts are private and that Google stopped indexing purchases when they redirected the old dashboard.
- **The History:** In 2019, an exposé revealed that Google kept an un-deletable 5-year ledger of all user receipts at `myaccount.google.com/purchases`. After global privacy backlash, Google quietly **killed and redirected that standalone web page**.
- **The Reality:** While the embarrassing public dashboard was removed, the backend machine-learning scraper was not. Receipt parsing continues via server-side machine learning under [Smart features and personalization in Gmail](https://support.google.com/mail/answer/10079371) to populate cross-service Google accounts data.

---

## Technical Boundaries & Limitations of Level 0

* **Audit vs. Remediation:** Recognizing these ten street-level extraction vectors establishes threat-model awareness; it does **not** retroactively scrub historical data already ingested by commercial data brokers or crowdsourced caller-ID directories.
* **Passive vs. Active Interception:** Physical surveillance traps (e.g., Xerox shop downloads or residential thermal shipping labels) require operational behavioral discipline rather than software toggles.
* **Scope of Countermeasures:** Technical, programmatic countermeasures against digital extraction (browser fingerprinting, encrypted DNS, radio scanning, and background daemons) begin systematically in Level 1 through Level 5.

---

## The Takeaway

None of this happens because you did something foolish or visited dangerous websites.

**It happens because consumer hardware and applications in India are configured by default for maximum corporate extraction.**

Now that the baseline reality is visible, we can begin systematically turning off these taps—starting with the simplest, zero-effort adjustments.

---
**Found this breakdown eye-opening?** Star this repository to help spread independent, zero-sponsored consumer education across India.
> **Reporting Changed Menus or Inaccuracies:**  
> Have you identified an interface path change on your phone or an updated regulatory circular? [Open an issue on GitHub](https://github.com/rack0911/digital-swaraj/issues) with your device manufacturer, model, and Android version.

---
**Proceed to [Level 1: The Zero-Effort Shield](01_LEVEL_ONE_BROWSER_AND_DNS.md)**
