# Level 1: The Zero-Effort Shield (Browser, Search & DNS) 

> **Document Status:** Verified (Current as of October 2026)  
> **Technical Baseline:** Android 13/14/15, Linux Kernel 6.x, Chromium / Gecko (Firefox ESR)  
> **Official Citations:** [RFC 7858 (DNS over TLS)](https://datatracker.ietf.org/doc/html/rfc7858), [RFC 8484 (DNS over HTTPS)](https://datatracker.ietf.org/doc/html/rfc8484), [CERT-In Directions No. 20(3)/2022-CERT-In](https://www.cert-in.org.in/PDF/CERT-In_Directions_70B_28.04.2022.pdf), [CCPA Guidelines for Prevention of Dark Patterns (2023)](https://consumeraffairs.nic.in/sites/default/files/CCPA_Notification.pdf)

---

> ###  Time Required: 10 Minutes | Difficulty: Beginner | Workflow Disruption: Zero
> 
> *The simplest, highest-leverage privacy upgrades require no behavioral sacrifice. In Level 1, we replace the three primary surveillance pipes on your phone and laptop: your browser, your search engine, and your DNS resolver.*

---

## The 60-Second Action Plan

| Vector | Current Vulnerable Default | The Zero-Effort Fix | Direct Result |
| :--- | :--- | :--- | :--- |
| **Mobile Browser** | Google Chrome | **Brave** or **Firefox** | Blocks network-level ad trackers, third-party cookie scripts, and fingerprinting probes. |
| **Desktop Isolation** | Standard Tabs | **Firefox Multi-Account Containers** | Traps trackers and sessions in isolated cookie vaults. |
| **Search Engine** | Google Search | **Brave Search** or **DuckDuckGo** | Eliminates sponsored fake customer care numbers and search profiling. |
| **Device DNS** | Plaintext Telecom ISP (Port 53) | **Android Private DNS (DoT)** | Encrypts all domain requests; blinds telecom ISP logging across mobile data. |
| **Home Network** | Default Wi-Fi Modem DNS | **Router-Level DNS (DHCP)** | Blocks ads and malware for the entire household (Smart TVs, family phones, IoT). |
| **Network Transit** | Unencrypted ISP Routing | **Zero-Log Offshore VPN** (Mullvad/Proton) | Bypasses ISP traffic inspection under CERT-In logging regulations. |

---

> [!TIP]
> **Quick Takeaway:**
> If you already use a hardened browser, an independent search engine, and encrypted DNS, **you are finished with Level 1.** 
> **[Jump straight to Level 2: Mobile Radio & Sensor Hygiene](02_LEVEL_TWO_RADIO_AND_SENSOR_HYGIENE.md)** to lock down background location and Bluetooth tracking. 
> *(Or scroll down to follow the step-by-step setup guides below.)*

---

## 1. The Browser Switch: Killing Tracking & Dynamic Pricing

Google Chrome is the default browser on over 85% of Android devices in India. Chrome does not block third-party cookies by default and is engineered by an advertising corporation to catalog your browsing habits.

### Recommended Privacy Browsers:
- **[Brave Browser](https://brave.com/) (Beginner Friendly):** Built on Chromium, so every website and extension works identically to Chrome. Comes out of the box with aggressive ad-blocking, tracker shielding, and fingerprint randomization.
- **[Firefox](https://www.mozilla.org/firefox/) (Community & FOSS):** Built on an independent Gecko engine. Supports open-source extensions on Android (like **uBlock Origin**) for ultimate control.

---

### Advanced Hardening: Firefox Multi-Account Containers 

On desktop workstations, websites track you across tabs using shared session cookies. If you open Facebook or Amazon in one tab and do personal research in another, third-party tracking scripts correlate your identity across both.

**The Solution:** Install the official **[Firefox Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/)** extension.
- **Cryptographic Cookie Sandboxes:** It separates your browser tabs into color-coded isolated containers (e.g., *Personal*, *Work*, *Banking*, *Shopping*).
- **Session Compartmentalization:** Cookies, local storage, and cache in your *Shopping* container cannot be accessed by tabs inside your *Personal* or *Work* containers. You can stay logged into Google in one container while keeping the rest of your web browsing completely invisible to Google's tracking scripts.

---

### Real-World Case Study: Defeating Dynamic Ticket Pricing 

When you search for a flight (e.g., Mumbai to Delhi) or train tickets on travel aggregators:
1. **Cookie Profiling:** Tracking pixels log your route, travel dates, and frequency of visits.
2. **False Urgency:** When you return from the same browser profile, dynamic pricing algorithms inflate the fare and display a flashing countdown: *"Only 2 seats left at this price!"*
3. **The Regulatory Reality:** Under the **Central Consumer Protection Authority (CCPA) Guidelines for Prevention of Dark Patterns (2023)**, manufacturing artificial urgency to coerce immediate purchases is classified as a deceptive practice.

### The Antidote:
- Always search flights and hotel bookings using a clean, hardened browser (Brave Private Window or Firefox with strict cookie isolation).
- When tracking cookies and fingerprinting probes are blocked, the booking engine treats you as a first-time visitor—preventing dynamic re-target surges.

---

### What Is Browser Fingerprinting? (Tracking You Without Cookies) 

Many users believe opening **"Incognito Mode"** on standard browsers makes them invisible to tracking. 

**It does not.** Traditional incognito mode only prevents your browser from saving local history and cookies on your phone. It does nothing to stop **Browser Fingerprinting**:

- **How It Works:** When you load a webpage, background JavaScript queries hardware and system parameters: your exact screen resolution, GPU model, WebGL rendering characteristics, audio latency, battery status, and available system fonts.
- **The Unique Hash:** Combined, these technical attributes produce a distinct statistical identifier (a device "fingerprint") that isolates your device among millions of internet users—even without cookies or an account login.
- **Why Hardened Browsers Fix This:**
 - **Brave** implements **fingerprint randomization ("farbling")**: every browsing session subtly injects randomized mathematical noise into canvas and audio outputs so tracker networks cannot correlate your activity.
 - **Firefox** standardizes system metrics so your browser looks indistinguishable from millions of other standard installations.

---

## 2. The Search Engine Switch: Killing Scam Customer Care Numbers

### The Risk of Default Google Search in India
In India, Google Search results have become an advertising minefield:
- The top 3 to 4 results for almost any commercial query are paid sponsored links.
- Cybercrime police across multiple states have repeatedly flagged **fake customer care numbers** running as sponsored Google Ads for delivery apps, domestic airlines, and banks. Victims searching for refund help click the top ad and end up transferring money to fraudsters.

### The Fix: Set Brave Search or DuckDuckGo as Default
1. Open your browser settings ➔ **Search Engine**.
2. Switch from Google to **Brave Search** or **DuckDuckGo**.
3. **The Difference:** Clean, independent index. Zero profiling, zero search history linked to your identity, and no sponsored scam call-center ads masquerading as organic results.

---

## 3. Encrypted DNS: Blinding Plaintext Network Logging

Every time you open an app or visit a website, your phone sends a **DNS query** (Domain Name System) to translate a human-readable domain name (like `github.com`) into a machine IP address.

### The Default Architecture: Unencrypted Plaintext (Port 53)
By default across commercial telecom operators and Internet Service Providers (ISPs), standard DNS queries are transmitted in unencrypted plaintext over **UDP Port 53** (a standard dating back to 1987 via RFC 1035).

Because traditional DNS lacks encryption, any intermediate network operator, public Wi-Fi router administrator, or network gateway can observe:
- The exact domain name of every web service or app your device attempts to contact.
- Precise timestamps and frequency of network requests.
- Hostnames queried across all background applications installed on your phone.

This plaintext visibility is what enables network-level traffic logging, domain redirection, and connection filtering at the gateway without cryptographic verification.

---

### Step 1: Enable Native Android Private DNS (Mobile Shield)

You do **not** need to install a heavy third-party VPN app that drains your battery. Android has native support for **DNS-over-TLS (DoT)** built directly into the operating system.

#### Setup in 60 Seconds:
1. Open your Android phone's **Settings**.
2. Tap **Network & internet** (or *Connections* on Samsung devices).
3. Tap **Private DNS** (often found under *More connection settings*).
4. Change from *Automatic / Off* to **Private DNS provider hostname**.
5. Enter one of the following verified privacy providers:

| Provider | Hostname to Enter | Best For |
| :--- | :--- | :--- |
| **NextDNS (Recommended)** | `dns.nextdns.io` | Ultra-fast, blocks ad trackers system-wide across all apps. |
| **Cloudflare Privacy DNS** | `one.one.one.one` | Global enterprise speed, zero logging audited independently. |
| **Control D (Ad-Blocking)** | `p2.freedns.controld.com` | Instant system-wide ad and malware blocking with zero account setup. |

6. Tap **Save**.

---

### Step 2: Protect the Entire Household: Router-Level DNS (Home Wi-Fi Modem)

Configuring Private DNS on your personal smartphone protects you when roaming. However, at home, your family's devices—Smart TVs running ad-heavy OEM software, non-technical parents' phones, gaming consoles, and smart home IoT gadgets—continue to transmit unencrypted plaintext queries through your home broadband provider (JioFiber, Airtel Xstream, ACT, BSNL).

#### How to Shield the Whole Home at the Gateway:
By updating the DNS addresses pushed by your home Wi-Fi modem's **DHCP Server**, every connected device in your household is protected automatically with zero software configuration needed on individual phones.

1. **Access Router Admin Portal:** Open your browser and navigate to your modem gateway IP (typically `192.168.1.1` or `192.168.0.1` printed on the sticker underneath your router). Log in with your admin credentials.
2. **Locate DHCP / DNS Settings:** Navigate to **Network** ➔ **LAN** / **DHCP Server** ➔ **DNS Settings**.
3. **Change Default ISP DNS to Privacy Resolvers:** Replace your telecom's default DNS IPs with privacy-respecting, ad-blocking resolvers:

| Privacy DNS Provider | Primary DNS (IPv4) | Secondary DNS (IPv4) | Features |
| :--- | :--- | :--- | :--- |
| **AdGuard DNS (Family Friendly)** | `94.140.14.14` | `94.140.15.15` | Blocks ads, phishing, and malware across all home devices. |
| **Control D (Uncensored Ad-Block)** | `76.76.2.2` | `76.76.10.2` | High-speed ad and telemetry blocking with zero configuration. |
| **Cloudflare Privacy** | `1.1.1.1` | `1.0.0.1` | Ultra-fast resolution with strict zero-logging policy. |

4. **Save & Reboot Router:** All devices connected to your home Wi-Fi now resolve domains through privacy-hardened resolvers—instantly killing banner ads on smart TVs and shielding your family's browsing from default ISP logging.

---

## 4. Advanced Network Defense: Zero-Log VPNs & The CERT-In Reality 

For high-risk environments (public café Wi-Fi, untrusted networks, or bypassing network-level ISP throttling), an encrypted Virtual Private Network (VPN) tunnels all internet traffic through an encrypted pipe.

### The Indian Regulatory Reality: CERT-In April 2022 Directives
On **April 28, 2022**, India's national cyber emergency agency (**CERT-In**, under MeitY) issued landmark cybersecurity directives (Directions under Section 70B of the IT Act):
- **Mandatory 5-Year User Logging:** Any VPN provider operating **physical servers within Indian territory** is legally compelled to collect, maintain, and surrender user personal records for 5 years—including verified subscriber names, physical residential addresses, contact phone numbers, assigned IP addresses, and timestamps.
- **The Impact on Privacy:** Under these rules, any commercial VPN running physical hardware in India cannot mathematically offer a true "no-logs" service.

### The Sovereign Response: Offshore Zero-Log Providers
In direct response to CERT-In mandates, verified international privacy VPNs shut down their physical server infrastructure in India and switched to virtual routing from offshore jurisdictions (Singapore, Switzerland, Sweden) to uphold their strict zero-log cryptographic guarantees:

| VPN Provider | Model | Jurisdictional Shield | Privacy Advantage |
| :--- | :--- | :--- | :--- |
| **[Mullvad VPN](https://mullvad.net/)** *(Gold Standard)* | Anonymous Account ID | Sweden | **Zero Personal Data:** Generates a random 16-digit account number. Requires no email, no name, and no phone number. Accepts cash via post or cryptocurrency. |
| **[Proton VPN](https://protonvpn.com/)** *(Best Free Tier)* | Free & Paid | Switzerland | **Swiss Data Laws:** Independently audited zero-logs policy; offers an unlimited free tier without data caps or speed throttling. |
| **[IVPN](https://www.ivpn.net/)** *(Open-Source Purist)* | Anonymous Account ID | Gibraltar | **100% Open-Source:** Requires zero email to sign up; independently audited annual no-log architecture. |

> **Usage Rule:** Use an offshore zero-log VPN when on public Wi-Fi or when researching sensitive topics, but disable it when accessing Indian PSU banking portals (SBI, PNB) or government tax portals to avoid automated anti-fraud IP security blocks.

---

## 5. Verification: Test Your Shield

To verify that your Level 1 defenses are functioning, open your new browser and visit these independent diagnostic tools:

1. **Ad & Tracker Diagnostic:** 
    **[adblock-tester.com](https://adblock-tester.com/)**  
    *Target Score:* **85 – 100 points** (Validates blocking of advertising servers, analytics scripts, banner ad networks, and OEM telemetry).

2. **EFF Fingerprint Diagnostic:** 
    **[coveryourtracks.eff.org](https://coveryourtracks.eff.org)**  
 *Target:* Verifies that your browser resists unique device fingerprinting.

---

## Technical Boundaries & Limitations of Level 1

* **DNS Encryption vs. Destination IP and SNI Exposure:** Encrypted DNS (DNS-over-TLS via RFC 7858 or DNS-over-HTTPS via RFC 8484) encrypts domain name resolution queries, preventing intermediate ISPs and local network sniffers from logging plaintext UDP Port 53 lookups. However, **DNS encryption does not conceal destination IP addresses**. Furthermore, during the subsequent TLS connection handshake, unless both the client and destination server support **Encrypted Client Hello (ECH / RFC 9460)**, the Server Name Indication (SNI) header is transmitted in plaintext, allowing an upstream network operator with deep-packet inspection (DPI) to identify the target domain.
* **Browser Isolation vs. Authenticated User Sessions:** Privacy-hardened browsers (Brave, Firefox with Multi-Account Containers) isolate cross-site cookies, randomize canvas/audio fingerprints, and strip URL referral parameters. However, **they do not anonymize activity conducted while logged into a central user account**. Logging into a personal Google, Amazon, or social media account inside an isolated container still associates all queries, clicks, and session timestamps directly with your account profile.
* **VPN Egress vs. Domestic Banking Services:** Commercial zero-log VPNs operating outside Indian jurisdiction tunnel traffic securely, masking your residential IP from destination web servers. However, major Indian public and private sector banks (SBI, HDFC, ICICI), UPI payment gateways, and statutory portals (Income Tax Department, EPFO) employ automated fraud-detection filters that routinely block or flag incoming traffic from foreign or commercial VPN datacenter IP ranges. Accessing these services frequently requires split-tunneling or temporary VPN suspension.
* **Router-Level DNS (Port 53 Fallback):** Setting custom DNS server IPs on a standard home Wi-Fi modem routes network queries away from default ISP resolvers for connected devices. However, standard consumer router firmware transmits these queries across the WAN interface using unencrypted **plaintext UDP Port 53** unless the router runs custom firmware (e.g., OpenWrt) with native DNS-over-TLS or a dedicated local encrypted forwarder (such as AdGuard Home or Pi-hole with upstream DoT).

---

## Completed Checklist

- [x] Primary browsing moved away from default Chrome to a tracker-blocking browser (Brave / Firefox).
- [x] Desktop sessions isolated using Firefox Multi-Account Containers.
- [x] Default search engine switched away from Google Search to an independent, non-tracking alternative.
- [x] Native Android Private DNS enabled with encrypted DNS-over-TLS.
- [x] Home Wi-Fi router DNS updated to shield household Smart TVs and family devices from ISP logging.
- [x] Verified zero-log VPN (Mullvad, Proton, or IVPN) kept on standby for public Wi-Fi networks.

---

### Verified System State Changes

Here are the concrete, technically verified shifts now active on your device:

1. **Eliminated Third-Party Script Bloat:** Media-heavy web pages no longer execute dozens of background tracker scripts, video overlays, or telemetry beacons—reducing network requests and eliminating intrusive ad layouts.
2. **Encrypted DNS Lookups:** Your domain resolution queries travel over encrypted TLS rather than plaintext UDP Port 53. Intermediate network operators cannot log, inspect, or tamper with your raw DNS requests at the resolver level.
3. **Household-Wide Protection:** Every device connected to your home broadband—including smart TVs with embedded telemetry—is shielded from ad networks and unencrypted ISP logging.
4. **Mitigated Retargeting Surges:** By blocking persistent tracking cookies and deploying fingerprint randomization, booking engines cannot easily recognize you as an urgent returning visitor to trigger retargeting price jumps.
5. **Regulatory Compliance Awareness:** You understand the CERT-In VPN legal landscape and know how to choose genuine zero-log tools that preserve mathematical privacy.

---
**Support the Project:** Star this repository on GitHub to help other Indian developers, students, and citizens discover it.
**Proceed to [Level 2: Mobile Radio & Sensor Hygiene](02_LEVEL_TWO_RADIO_AND_SENSOR_HYGIENE.md)**
