# SecITred_tools
RedTeam Go Toolkit — Tool Instructions

Important Notice
This toolkit is intended only for ethical security testing, defensive research, and incident response activities.
Use only on systems you own or have explicit permission to test.
The authors take no responsibility for misuse.
<img width="2553" height="1009" alt="RedTools" src="https://github.com/user-attachments/assets/b8d90846-a135-41a1-8e44-ad0ab45ffd42" />

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
