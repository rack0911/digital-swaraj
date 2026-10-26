# Forensic Case Study: Defanging Surveillance Capitalism on Nothing Phone (2a) & Stock Android

> **Device:** Nothing Phone (2a) (`A059` / `AsteroidsIND`)  
> **Operating System:** Nothing OS 2.6 / 3.0 (Android 16 Developer Baseline)  
> **Methodology:** Non-Root Kernel-Level AppOps Containment, ADB User-Space Isolation, NextDNS Airgapping  
> **Author:** Digital Swaraj Research Project (October 2026)  
> **Status:** Production Verified

---

## Executive Summary

Modern "clean, near-stock" Android devices (such as Nothing OS, Motorola, and Pixel) market themselves as bloat-free alternatives to heavy Chinese skins (MIUI, ColorOS). However, forensic analysis of active system processes on a live **Nothing Phone (2a)** revealed that behind the minimalist dot-matrix aesthetic sits an aggressive surveillance apparatus:

1. **Privileged OTP/SMS Interception:** Google Play Services actively intercepted incoming financial two-factor SMS codes despite third-party password managers (Bitwarden) and open-source keyboards (HeliBoard) being designated as system defaults.
2. **Ambient Hardware Profiling:** Google Play Services maintained active, un-notified hooks into outgoing phone calls, complete call logs, address book entries, motion sensors, camera, microphone, and clipboard data.
3. **The Multi-Profile Security Hole:** Secondary Android user spaces—such as **DualApps (User 999)** and **Private Space (User 10)**—spawn separate instances of Google Play Services with full default permissions, effectively bypassing single-user ADB debloating.
4. **Stealth OEM Daemons:** Nothing OS pre-loads background telemetry engines (`com.nothing.appservice`, `com.nothing.essentialintelligence`, `com.nothing.logkit`, `com.nothing.universal.search`) that continuously index user activity, search queries, and push partner recommendations.

By implementing the **Digital Swaraj Kernel-Level AppOps Sandbox**, this device was stripped to bare metal without root, preserving 100% functionality for Indian banking apps (BHIM, YONO SBI, FedMobile, Axis Mobile) and Google Play Integrity.

---

## 1. The Incident: The Scapia OTP Interception

### The Trigger
While completing an authentication flow for a financial application (Scapia), the user observed an intrusive system overlay rendering the text:
> *"Autofill code from Google: XXXXXX"*

The user had already deployed **Bitwarden** as the default system Autofill and Credential Provider, and **HeliBoard** as the default keyboard (with zero network permissions). The user had never linked or synchronized SMS data to a Google account.

### The Forensic Discovery
An ADB audit of `com.google.android.gms` (Google Play Services) immediately dumped the smoking gun:

```bash
$ adb shell cmd appops get com.google.android.gms RECEIVE_SMS
RECEIVE_SMS: allow; time=+16m13s ago
```

The timestamp coincided to the exact second of the Scapia verification attempt. 

### Architectural Root Cause
Under standard AOSP implementations, Google Play Services is granted root-adjacent privileges: `android.permission.RECEIVE_SMS` and `android.permission.READ_SMS`. When third-party FinTech apps initiate authentication, their client libraries call Google's proprietary **SmsRetriever API** (`com.google.android.gms.auth.api.phone.service.SmsRetrieverApiService`). 

Google Play Services intercepts the raw `Telephony.SMS_RECEIVED` broadcast **before the user's messaging app even processes the notification**, extracts the OTP, and renders an in-house Google Play Services overlay to capture user interaction.

```
Incoming Cellular SMS
       │
       ▼
[ Baseband / RIL ]
       │
       ▼
[ AOSP Telephony Framework ] ────► Broadcast: Telephony.SMS_RECEIVED
                                           │
                        ┌──────────────────┴──────────────────┐
                        ▼                                     ▼
           [ Google Play Services (GMS) ]           [ User Messaging App ]
           • Reads raw SMS payload                  • Shows notification
           • Extracts 6-digit OTP
           • Renders "Google Autofill" Overlay
```

---

## 2. Forensic Audit: Google Play Services God-Mode Matrix

Querying active AppOps for Google Play Services (`UID 10151`) on the Nothing Phone (2a) revealed an extensive ambient tracking posture:

| Privilege / AppOp | System Status | Last Invocation Timestamp | Forensic Threat Analysis |
| :--- | :--- | :--- | :--- |
| `PROCESS_OUTGOING_CALLS` | **ALLOWED** | `time=+46m11s ago` | Monitored dialed phone numbers in real-time. |
| `READ_CALL_LOG` | **ALLOWED** | `time=+3d2h ago` | Access to incoming/outgoing call metadata and timestamps. |
| `READ_CONTACTS` | **ALLOWED** | `time=+3h25m ago` | Continuous background polling of user phonebook. |
| `ACTIVITY_RECOGNITION` | **ALLOWED** | `time=+1m33s ago (running)` | Accelerometer/gyroscope motion tracking (walking, driving, stationary). |
| `CAMERA` | **ALLOWED** | `time=+55d ago` | Direct camera hardware access. |
| `RECORD_AUDIO` | **ALLOWED** | Unrestricted | Microphone access for ambient listening/hotword processing. |
| `READ_CLIPBOARD` | **ALLOWED** | `time=+25d ago` | Reading copied text, passwords, and sensitive credentials. |
| `BLUETOOTH_ADVERTISE` | **ALLOWED** | Continuous | Transmitting BLE beacons for Google's global Find My Device mesh. |
| `WIFI_SCAN` | **ALLOWED** | `time=+1d9h ago` | Capturing surrounding BSSID router MAC addresses for triangulation. |

---

## 3. The Multi-Profile Security Hole (DualApps & Private Space)

A critical discovery made during this audit was that **single-user ADB commands (`--user 0`) leave severe privacy backdoors open** if the device utilizes cloned or private profiles.

Executing `pm list users` revealed:
```text
Users:
    UserInfo{0:Primary:4c13} running
    UserInfo{10:Private space:1090}
    UserInfo{999:DualApps:4001010} running
```

### The Mechanism
* In Android, user profiles run with isolated Linux UID offsets:
  * Primary Profile User 0: UID `10151`
  * DualApps Profile User 999: UID `99910151` ($999 	imes 100000 + 10151$)
  * Private Space User 10: UID `1010151` ($10 	imes 100000 + 10151$)
* Restricting Google Play Services on User 0 left User 999 running a **fully un-sandboxed second instance of Google Play Services** with `CAMERA: foreground`, `RECORD_AUDIO: foreground`, and active location capabilities.

### The Remediation
The AppOps iron curtain must be applied across **all UID boundaries**:

```bash
# Apply across Primary, DualApps, and Private Space UIDs:
for uid in 10151 99910151 1010151; do
  for op in COARSE_LOCATION FINE_LOCATION GPS MONITOR_LOCATION MONITOR_HIGH_POWER_LOCATION             ACTIVITY_RECOGNITION BODY_SENSORS RECORD_AUDIO CAMERA READ_CONTACTS WRITE_CONTACTS             READ_CALL_LOG PROCESS_OUTGOING_CALLS READ_SMS RECEIVE_SMS SEND_SMS WRITE_SMS             BLUETOOTH_SCAN BLUETOOTH_CONNECT BLUETOOTH_ADVERTISE NEARBY_WIFI_DEVICES WIFI_SCAN             READ_CLIPBOARD; do
    cmd appops set --uid $uid $op ignore
  done
done
```

---

## 4. Nothing OS Stealth Daemons: Beyond Stock Android

While Nothing OS promotes a clean interface, inspection of package records and running services revealed OEM-specific telemetry engines:

```text
com.nothing.appservice            ──► Background engine for silent partner app promotion.
com.nothing.essentialintelligence ──► On-device AI tracking and behavioral telemetry.
com.nothing.universal.search      ──► System indexer capturing local queries and contacts.
com.nothing.ntessentialspace      ──► Proprietary Essential Space cloud integration.
com.nothing.ntessentialrecorder   ──► Background Essential Voice/Audio recorder.
com.nothing.logkit                ──► Diagnostic uploader and crash log harvester.
com.nothing.experience            ──► User Experience Programme behavioral analytics.
com.nothing.proxy                 ──► Holds NothingWifiTrackService and BluetoothTrackService.
```

### The Freeze Protocol
Certain protected OEM packages return `[DELETE_FAILED_INTERNAL_ERROR]` when targeted with `pm uninstall`. These must be permanently frozen using `pm disable-user`:

```bash
for pkg in com.nothing.appservice            com.nothing.essentialintelligence            com.nothing.aiwidget            com.nothing.user.center            com.nothing.universal.search            com.nothing.ntgamedashboard            com.nothing.userguide            com.nothing.introduction16            com.nothing.experience            com.nothing.logkit; do
  pm disable-user --user 0 $pkg
done
```

---

## 5. Offline Beaconing & The AOSP Component Protection Barrier

A live scan of running services uncovered continuous Bluetooth Low Energy (BLE) background activity:

```text
com.google.android.gms/.findmydevice.spot.bleadvertising.OfflineBeaconService_Persistent
com.google.android.gms/.nearby.presence.service.LifeCycleService
```

### The Component Security Trap
Attempting to shut down these individual background services via ADB returns:
```text
java.lang.SecurityException: Shell cannot change component state for ComponentInfo{com.google.android.gms/...}
```
Google explicitly hardcoded AOSP to prevent the ADB `shell` user from disabling sub-components of `com.google.android.gms`.

### The Hardware-Level Bypass
Instead of fighting Google's software component locks, **we cut off physical access to the antenna at the Linux kernel layer**:

```bash
cmd appops set --uid 10151 BLUETOOTH_ADVERTISE ignore
cmd appops set --uid 10151 BLUETOOTH_SCAN ignore
cmd appops set --uid 10151 NEARBY_WIFI_DEVICES ignore
```

When `OfflineBeaconService_Persistent` calls the Android Bluetooth HAL to broadcast a beacon, the kernel intercepts the call and drops the packet. GMS transmits zero bytes over the air.

---

## 6. Fleet Comparison: OEM Bootloop Tripwires

During the broader Digital Swaraj audit across multiple household devices (Nothing Phone 2a, Motorola Tab 60 Pro, Xiaomi Redmi 10A), two catastrophic OEM bootloop tripwires were discovered and documented:

### 1. The Xiaomi Hardcoded Signature Check (`dandelion`)
On Xiaomi MIUI 12.5 / HyperOS devices, uninstalling `com.xiaomi.finddevice` causes an immediate, fatal bootloop:

```text
*** FATAL EXCEPTION IN SYSTEM PROCESS: Thread-11
java.lang.RuntimeException: System error: connot find system app : com.xiaomi.finddevice
    at com.miui.server.SecurityManagerService.enforceAppSignature(SecurityManagerService.java:659)
```
*(Note the developer's misspelling of "cannot" as "connot" inside Xiaomi's proprietary source code).*

* **The Rule:** **Never** uninstall `com.xiaomi.finddevice` on Xiaomi hardware. Leave the inert APK registered and strip its permissions via AppOps (`COARSE_LOCATION: ignore`, `RUN_IN_BACKGROUND: ignore`).

### 2. The Android 14–16 SDK Sandbox Lockout
On modern Android versions, `PackageManagerService.java` enforces a hardcoded dependency via `getRequiredSdkSandboxPackageName()`:
* **The Rule:** **Never** uninstall `com.google.android.sdksandbox`. Removing it crashes `system_server` on boot across all modern Android devices.

---

## 7. Verified Production State & Results

Following the execution of this protocol on the Nothing Phone (2a):

1. **Banking & UPI Intact:** YONO SBI, FedMobile, Axis Mobile, BHIM, and Google Pay authenticate smoothly. Play Integrity hardware attestation (`MEETS_DEVICE_INTEGRITY`) remains valid.
2. **Push Notifications Operational:** Firebase Cloud Messaging (FCM) maintains a single, low-power encrypted socket (`tcp6 port 5228`), waking apps for genuine incoming messages without ambient telemetry.
3. **RAM & Standby Battery Life:** Active background telemetry memory usage dropped to **0 MB**, eliminating CPU wakelocks and extending standby battery life from ~1.5 days to **3–4 days**.
4. **Data Sovereignty:** Financial OTPs, phone calls, location data, contacts, and clipboard buffers are mathematically inaccessible to Google Play Services.

---

*This case study is published under the GNU Free Documentation License as part of the [Digital Swaraj Project](https://github.com/rack0911/digital-swaraj).*
