# Level 2: Mobile Radio & Sensor Hygiene (Hardware Containment)

> **Document Status:** Verified (Current as of October 2026)  
> **Technical Baseline:** Android 13/14/15, One UI 6+, HyperOS 1.0+, ColorOS 14+, Funtouch OS 14+  
> **Official Citations:** [Android Developer: WifiManager.isScanAlwaysAvailable()](https://developer.android.com/reference/android/net/wifi/WifiManager#isScanAlwaysAvailable()), [Android BluetoothLeScanner API](https://developer.android.com/reference/android/bluetooth/le/BluetoothLeScanner), [Android SensorManager Documentation](https://developer.android.com/reference/android/hardware/SensorManager)

---

> ###  Time Required: 10 Minutes | Difficulty: Beginner | Workflow Disruption: Zero
> 
> *Level 2 moves beneath the browser to the physical hardware. Modern mobile operating systems are configured by default to keep radio transmitters and motion sensors active in the background—even when you toggle them "Off" in the notification shade. In 10 minutes, we will shut down background radio probing, eliminate lockscreen clickbait bloatware, and restrict sensor access.*

---

## The 60-Second Action Plan

| Vector | Current Vulnerable Default | The Zero-Effort Fix | Result |
| :--- | :--- | :--- | :--- |
| **Phantom Radios** | Wi-Fi & Bluetooth Scanning enabled 24/7 | Toggle **OFF** in *Location Services* | Stops hardware probe packets from pinging commercial beacons when toggles are "Off". |
| **Location Telemetry** | Google Location Accuracy (Network Triangulation) | Toggle **OFF** | Stops sending nearby Wi-Fi network BSSIDs and cell IDs to external location servers. |
| **Lockscreen Bloat** | Glance / Lock Screen Magazine enabled by OEM | Set Wallpaper Services to **None** | Completely removes lockscreen clickbait news, ads, and accidental swipe activations. |
| **Background Sensors** | "Physical Activity" & "Nearby Devices" granted | Revoke for non-fitness / casual apps | Prevents apps from profiling whether you are walking, driving, or stationary. |

---

> [!TIP]
> **Quick Takeaway:**
> If you already configured these settings from the table, **you are finished with Level 2.** 
> **[Jump straight to Level 3: GAFAM Account Surgery](03_LEVEL_THREE_ACCOUNT_SURGERY.md)** to audit and defang Google and LinkedIn account scrapers. 
> *(Or scroll down to follow the step-by-step OEM-specific walkthroughs below.)*

---

## 1. Disabling Phantom Radios (Wi-Fi & Bluetooth Background Scanning)

### The Deception of Quick Settings
When you swipe down your phone's notification panel and tap the Wi-Fi or Bluetooth icons to "Off", the Android operating system **does not shut down the physical radio transceivers.**

It merely disconnects from your current router or headphones. In the background, the hardware continues sending probe request frames 24 hours a day to scan for nearby routers and Bluetooth Low Energy (BLE) commercial beacons located in retail outlets, transit stations, and airports.

### How to Turn It Off Completely:
1. Open phone **Settings**.
2. Navigate to **Location** ➔ **Location Services** (on some devices: *Security & Location* or *Privacy*).
3. Locate these two settings:
 - **Wi-Fi Scanning:** *"Let apps and services scan for Wi-Fi networks at any time, even when Wi-Fi is off."*
 - **Bluetooth Scanning:** *"Let apps and services scan for nearby devices at any time, even when Bluetooth is off."*
4. Toggle **BOTH to OFF**.

**The Technical Shift:** When you switch Wi-Fi or Bluetooth to "Off" in the Quick Settings panel, the physical hardware will now actually stop emitting probe frames.

---

## 2. Google Location Accuracy vs. True GPS 

### Understanding Network Location vs. Satellite GPS
Android phones determine location using two distinct methods:
1. **Passive Satellite GPS:** Your phone's GPS antenna passively listens to radio signals broadcast from satellites in orbit. Listening to satellite signals transmits zero data back to any server.
2. **Google Location Accuracy (GLS):** To estimate location faster indoors, your phone scans every Wi-Fi network BSSID and cell tower within range and transmits that telemetry to Google's crowdsourced location database.

### How to Enforce Pure On-Demand GPS:
1. Open **Settings** ➔ **Location** ➔ **Location Services**.
2. Tap **Google Location Accuracy**.
3. Toggle it to **OFF**.

**What Happens:** 
Navigation apps (Google Maps, ride-hailing services) will continue functioning normally using satellite GPS when opened. However, your device will stop continuously transmitting the MAC addresses of your home, office, and neighbor's Wi-Fi routers to central databases.

---

## 3. Disabling Lockscreen Clickbait (Glance & Lockscreen Stories)

In India, budget and mid-range devices from major manufacturers (Samsung Galaxy M/F series, Xiaomi Redmi, Realme, Vivo, and Oppo) ship with third-party lockscreen advertising services—most prominently **Glance** or **Lock Screen Magazine**—enabled out of the box.

### The Problem:
Every time you tap the power button to check the time, you are served full-screen sponsored content, clickbait news, and commercial teasers that consume background mobile data and encourage impulsive browsing.

### How to Disable It Permanently:

#### On Samsung (One UI):
1. Open **Settings** ➔ **Lock screen**.
2. Tap **Wallpaper services** (or *Lock screen wallpaper services*).
3. Select **None** (switch away from *Glance on Samsung*).
4. Toggle off **Swipe left for glance**.

#### On Xiaomi / Redmi / POCO (MIUI / HyperOS):
1. Open **Settings** ➔ **Always-on display & Lock screen**.
2. Scroll to **Glance for Mi**.
3. Toggle it to **OFF**.

#### On Realme / Oppo / Vivo (ColorOS / Funtouch OS):
1. Open **Settings** ➔ **Home screen & Lock screen**.
2. Tap **Lock Screen Magazine** (or *Glance*).
3. Toggle it to **OFF**.

---

## 4. High-Risk Sensor Permissions Audit

Mobile operating systems have introduced specialized permissions that casual apps abuse to track real-world user habits:

### A. "Physical Activity" (Motion & Step Tracking)
- **What It Does:** Uses hardware accelerometer and gyroscope data to calculate whether you are stationary, walking, running, or riding in a vehicle.
- **The Risk:** E-commerce, delivery, and social media apps use this to detect commute patterns and physical movement states.
- **Action:** Go to `Settings ➔ Apps ➔ Permission Manager ➔ Physical Activity`. Revoke access from every app except dedicated health/fitness trackers.

### B. "Nearby Devices" (BLE Beacon Probing)
- **What It Does:** Allows apps to discover and interact with Bluetooth devices without requesting fine GPS location permission.
- **The Risk:** Commercial apps use nearby device access to detect proximity to other users and indoor retail beacons.
- **Action:** Go to `Settings ➔ Apps ➔ Permission Manager ➔ Nearby devices`. Revoke access from shopping, food delivery, and social apps that do not require audio accessories.

### C. Microphone & Camera Hygiene
- Go to `Settings ➔ Apps ➔ Permission Manager ➔ Microphone` (and *Camera*).
- Ensure every granted app is set strictly to **"Ask every time"** or **"Allow only while using the app"**.
- Ensure **zero apps** have permission set to *"Allow all the time"*.

---

## Technical Boundaries & Limitations of Level 2

* **Cellular Tower Triangulation (Telco Law):** Disabling Wi-Fi/Bluetooth background scanning and Google Location Accuracy stops *device-side* crowdsourced telemetry from uploading nearby BSSIDs and cell IDs to tech platforms. However, it **does not and cannot prevent cellular tower triangulation by your telecom service provider** (Jio, Airtel, Vi, BSNL). Under the Indian Telegraph Act, 1885 / Telecommunications Act, 2023, and Department of Telecommunications (DoT) license mandates, cellular network operators continuously log the cell tower IDs and Timing Advance (TA) metadata of every connected SIM card for emergency routing and lawful interception.
* **Assisted GPS (A-GPS) Cold-Lock Times:** Disabling Google Location Accuracy switches your device to autonomous GNSS (GPS, GLONASS, Galileo, NavIC). Inside dense concrete buildings, basements, or urban canyons where direct line-of-sight to orbiting satellites is obstructed, initial satellite fix ("cold-lock") may take 15 to 45 seconds longer compared to Wi-Fi-assisted triangulation.
* **Motion Sensors vs. Sensor Rate Limiting:** Revoking the `ACTIVITY_RECOGNITION` permission prevents apps from querying Android's high-level activity recognition API (e.g. `STILL`, `WALKING`, `IN_VEHICLE`). Android 12+ limits high-frequency sensor sampling (`SENSOR_DELAY_FASTEST` capped at 200 Hz for unprivileged apps), but physical orientation can still be sampled by foreground apps unless sensors are toggled off globally via the Developer Quick Settings "Sensors Off" tile.

---

## Completed Checklist

- [x] Background Wi-Fi Scanning and Bluetooth Scanning disabled.
- [x] Google Location Accuracy disabled (pure on-demand satellite GPS enforced).
- [x] Lockscreen advertising bloatware (Glance / Magazine) permanently disabled.
- [x] "Physical Activity" and "Nearby Devices" permissions revoked from non-essential apps.
- [x] Microphone and Camera permissions restricted strictly to active in-app use.

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your device:

1. **Passive Wireless Radios:** When Wi-Fi and Bluetooth toggles are set to "Off", the transceivers stop transmitting probe requests into public spaces, mitigating beacon proximity logging.
2. **Private Location Determination:** Your phone relies on passive satellite GPS signals when you navigate, rather than continuously uploading local Wi-Fi router BSSIDs to external crowdsourced location databases.
3. **Clean, Calm Hardware Interface:** The lockscreen is restored to a neutral display. No accidental swipes into sponsored news, no battery drain from lockscreen video streams, and no commercial teasers greeting you every time you check the time.
4. **Motion Telemetry Contained:** Social, utility, and shopping apps can no longer poll accelerometer motion sensors to profile whether you are sitting, walking, or commuting.

---
**Support the Project:** Star this repository on GitHub to help other Indian developers, students, and citizens discover it.
**Proceed to [Level 3: GAFAM Account Surgery](03_LEVEL_THREE_ACCOUNT_SURGERY.md)**
