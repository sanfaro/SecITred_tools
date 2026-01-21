# SecITred_tools
RedTeam Go Toolkit — Tool Instructions

<img width="2553" height="1009" alt="RedTools" src="https://github.com/user-attachments/assets/b8d90846-a135-41a1-8e44-ad0ab45ffd42" />

# SecITRed 

[![Go Version](https://img.shields.io/github/go-mod/go-version/YourUsername/SecITRed)](https://golang.org/)

[![Platform](WEB)

[English Version](#english-version) | [ Wersja Polska](#wersja-polska)

---

<div id="english-version"></div>

##  English Version

### What is SecITRed?
**SecITRed** is an All-in-One security toolbox designed to act as a **daily HUB for SOC Analysts, Blue Teams, and Red Teams**. It functions as a lightweight, local web server that aggregates essential crypto, OSINT, and network utilities into a single, cohesive interface.

Think of it as your **personal cyber-workshop**—a place where you can quickly decode data, check IP reputation, generate payloads, and chain operations together without juggling ten different browser tabs and CLI tools.

###  Key Features

*   **⚡Single Binary:** Written in Go, compiles to a standalone executable with zero dependencies. No installation required.
*   ** Plugin System:** Extend functionality easily using JSON files. Wrap any external tool (Nmap, Python scripts, curl) and use it directly from the UI.
*   ** Pipeline Mode:** Chain multiple tools together (e.g., *Base64 Decode -> Extract IPs -> Scan Ports*) just like in CyberChef.
*   ** Essential Tools:**
    *   **Crypto:** Base64, XOR, Caesar, ROT13, SHA256, HashID.
    *   **Recon/OSINT:** Shodan, VirusTotal, AbuseIPDB, CRT.sh (Subdomains), DNS Records, Whois.
    *   **Red Team:** Reverse Shell Generator, Port Scanner.
    *   **Blue Team:** Email Header Analyzer (Phishing), JWT Debugger, HTTP Headers.
*   ** Observability:** Live system logs console built directly into the UI.
*   ** Privacy:** Runs locally on `localhost:8080`. Your data stays on your machine (unless you query external APIs).

### Installation

#### Option 1: Download Binary
Go to the [Releases](https://github.com/sanfaro/SecITred_tools) page and download the version for your OS (Windows/Linux/macOS).

#### Option 2: Build from Source
Requirements: Go 1.21+
```bash
git clone https://github.com/sanfaro/SecITred_tools.git
cd SecITRed
go run main.go
# OR build
go build -o SecITRed main.go





 CRYPTO / ENCODING TOOLS
- Echo

Description:
Returns the exact input without modification. Useful for testing pipelines, UI, and batch execution.

Input:
Any text

API Key:
Not required

Use cases:

Debugging

Pipeline validation

- Caesar Cipher


Description:
Applies a Caesar shift cipher to the input text.

Input:
Plaintext

Key:
Shift value (integer)

Use cases:

Basic cryptography demonstrations

Legacy cipher decoding

- ROT13

Description:
Applies the ROT13 substitution cipher.

Input:
Text

Key:
Not required

Use cases:

Obfuscation

CTF challenges

- XOR Cipher

Description:
Applies XOR encryption/decryption using a provided key.

Input:
Text

Key:
XOR key (string)

Use cases:

Malware analysis

Payload obfuscation

- Base64 Encode

Description:
Encodes input data using Base64.

Input:
Text or binary data

Key:
Not required

Use cases:

Data transport

Encoding payloads

- SHA256 Hash

Description:
Computes a SHA-256 cryptographic hash of the input.

Input:
Text

Key:
Not required

Use cases:

File integrity checks

IOC generation

 WEB / OSINT / THREAT INTELLIGENCE
- VirusTotal

Description:
Queries VirusTotal for threat intelligence related to an IP address.

Input:
IP address

API Key:
Required (VirusTotal API v3)

Output:
Detection statistics, reputation, and analysis data.

External Report:
Opens the VirusTotal GUI page for the IP.

Use cases:

Malware investigation

IOC validation

- AbuseIPDB

Description:
Checks an IP address against AbuseIPDB for abuse reports.

Input:
IP address

API Key:
Required

Output:
Abuse confidence score, report history.

External Report:
Direct link to AbuseIPDB IP report.

Use cases:

SOC triage

Blocking decisions

- Shodan

Description:
Retrieves open service and exposure data from Shodan.

Input:
IP address

API Key:
Required

Output:
Open ports, banners, vulnerabilities.

External Report:
Link to Shodan host page.

Use cases:

Attack surface mapping

Red team reconnaissance

- AlienVault OTX

Description:
Queries AlienVault Open Threat Exchange for IP intelligence.

Input:
IP address

API Key:
Optional (recommended)

Output:
Pulse data, threat reputation.

External Report:
OTX indicator page.

Use cases:

Threat hunting

SOC enrichment

- GreyNoise

Description:
Determines whether an IP address is part of background internet noise.

Input:
IP address

API Key:
Required

Output:
Classification (benign scanning vs targeted attack).

External Report:
GreyNoise visualization page.

Use cases:

Alert triage

False positive reduction

- SecurityTrails

Description:
Provides DNS and domain infrastructure intelligence.

Input:
Domain name

API Key:
Required

Output:
DNS history, subdomains, hosting data.

External Report:
SecurityTrails domain view.

Use cases:

Infrastructure mapping

Domain investigations

- URLScan.io

Description:
Submits a URL for dynamic analysis and behavior inspection.

Input:
URL

API Key:
Required

Output:
Scan ID and metadata.

Use cases:

Phishing investigation

Web malware analysis
