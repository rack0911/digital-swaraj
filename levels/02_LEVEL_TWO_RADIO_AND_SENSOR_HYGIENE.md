# Level 2: Mobile Radio & Sensor Hygiene (Hardware Containment)

> **Document Status:** Verified (Current as of October 2026)  
> **Supported Device Scope:** Android 12, 13, 14, 15 (Stock/Pixel, Samsung One UI 5/6, Xiaomi MIUI 14 / HyperOS, ColorOS/OxygenOS 13/14, Vivo Funtouch OS 13/14, Nothing OS 2.5/3.0)  
> **Primary Technical Citations:** [Android Developer: WifiManager.isScanAlwaysAvailable()](https://developer.android.com/reference/android/net/wifi/WifiManager#isScanAlwaysAvailable()), [AOSP Wi-Fi MAC Randomization Specification](https://source.android.com/docs/core/connect/wifi-mac-randomization), [Android Developer: Bluetooth Permissions in Android 12+](https://developer.android.com/develop/connectivity/bluetooth/bt-permissions), [Android Developer: Wi-Fi Scan Throttling](https://developer.android.com/develop/connectivity/wifi/wifi-scan#wifi-scan-throttling)

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

## 1. Background Radio Scanning Across Android Versions

### The Architectural Reality: What Happens When Radios Are "Off"?
When you swipe down your Android notification shade and toggle Wi-Fi or Bluetooth "Off", the operating system disconnects from your current access point or wireless peripheral. However, **it does not power down background radio scanning**.

* **`WifiManager.isScanAlwaysAvailable()` (Introduced in Android 4.3):** Under standard system defaults, Android enables an API method called [`isScanAlwaysAvailable()`](https://developer.android.com/reference/android/net/wifi/WifiManager#isScanAlwaysAvailable()). This allows internal location providers and third-party apps holding location permissions to scan for nearby Wi-Fi network access points even when the user toggle is set to "Off".
* **The Role of MAC Address Randomization:** Modern Android versions (Android 10, 11, 12, 13, 14, and 15) deploy [AOSP MAC Address Randomization](https://source.android.com/docs/core/connect/wifi-mac-randomization) for disconnected probe requests and connected networks. This prevents external Wi-Fi sniffers from tracking your physical hardware MAC address.
* **The Real Tracking Vector: Crowdsourced Telemetry:** Even though your MAC address is randomized, background Wi-Fi scanning actively captures the **BSSIDs (MAC addresses) and signal strengths (RSSI) of all nearby Wi-Fi routers**. Google Location Accuracy (GLS) periodically uploads these observed BSSID snapshots to Google's central database, determining your precise location without turning on the power-hungry satellite GPS receiver.
* **Bluetooth Low Energy (BLE) Scanning in Android 12+:** In Android 12 and higher, Google separated Bluetooth into dedicated runtime permissions ([`BLUETOOTH_SCAN`](https://developer.android.com/develop/connectivity/bluetooth/bt-permissions), `BLUETOOTH_CONNECT`, and `BLUETOOTH_ADVERTISE`). However, apps without the `neverForLocation` flag still utilize background BLE scanning to calculate physical proximity to commercial beacons in retail stores, transit stations, and airports.
* **Scan Throttling Limits:** To protect battery life, Android enforces [Wi-Fi scan throttling](https://developer.android.com/develop/connectivity/wifi/wifi-scan#wifi-scan-throttling): foreground apps are restricted to 4 scans per 2-minute window, and background apps are throttled to 1 scan every 30 minutes. However, system location services bypass these limits to maintain continuous tracking.

---

### Step-by-Step OEM Navigation Guide:
Because manufacturer interfaces structure location settings differently, use the exact navigation path for your device:

#### Google Pixel / Motorola / Nothing OS / Stock Android (Android 12/13/14/15):
1. Open **Settings** ➔ **Location**.
2. Tap **Location Services**.
3. Locate **Wi-Fi scanning** and **Bluetooth scanning**.
4. Toggle **BOTH to OFF**.

#### Samsung Galaxy Devices (One UI 5.x / 6.x):
1. Open **Settings** ➔ **Location**.
2. Tap **Location services** (under *Location requests*).
3. Tap **Wi-Fi scanning** ➔ Toggle **OFF**.
4. Tap **Bluetooth scanning** ➔ Toggle **OFF**.

#### Xiaomi / Redmi / POCO (MIUI 14 / Xiaomi HyperOS):
1. Open **Settings** ➔ **Location**.
2. Tap **Wi-Fi and Bluetooth scanning** (or *Location services*).
3. Toggle off **Wi-Fi scanning**.
4. Toggle off **Bluetooth scanning**.

#### OnePlus / Realme / Oppo (OxygenOS / ColorOS 13/14 / Realme UI):
1. Open **Settings** ➔ **Location**.
2. Tap **Wi-Fi and Bluetooth scanning**.
3. Toggle off **Wi-Fi scanning** and **Bluetooth scanning**.

#### Vivo / iQOO (Funtouch OS 13/14):
1. Open **Settings** ➔ **Location**.
2. Tap **Location services**.
3. Toggle off **Wi-Fi scanning** and **Bluetooth scanning**.

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
> **Reporting Changed Menus or Inaccuracies:**  
> Have you noticed a modified settings hierarchy or a different menu title on your specific manufacturer build? [Open an issue on GitHub](https://github.com/rack0911/digital-swaraj/issues) specifying your phone model and OEM skin version.

---
**Proceed to [Level 3: GAFAM Account Surgery](03_LEVEL_THREE_ACCOUNT_SURGERY.md)**
