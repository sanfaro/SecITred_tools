# SecITred_tools
RedTeam Go Toolkit — Tool Instructions

 **Disclaimer / Zrzeczenie się odpowiedzialności
This tool is intended for legal security analysis, authorized testing, and educational purposes only. The authors are not responsible for any misuse of this software.

Narzędzie służy wyłącznie do legalnej analizy bezpieczeństwa, autoryzowanych testów i celów edukacyjnych. Autorzy nie ponoszą odpowiedzialności za niewłaściwe wykorzystanie oprogramowania.
**


<img width="2553" height="1009" alt="RedTools" src="https://github.com/user-attachments/assets/b8d90846-a135-41a1-8e44-ad0ab45ffd42" />
(ver 0.1)
<img width="2541" height="1234" alt="RedTools" src="https://github.com/user-attachments/assets/a3b3d95f-397e-4d0d-89f0-02debe0d94e0" />
(ver 0.11)


# SecITRed 


[![Go Version](version go1.25.5)](https://golang.org/)


# SecITRed - Cyber Security Toolkit 

[![Go Version](https://img.shields.io/badge/Go-1.21%2B-blue)](https://golang.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](https://github.com/)

# SecITRed

Cybersecurity Swiss Army Knife for SOC & Red Teams.
A standalone, local web-based toolkit for data decoding, OSINT, and malware analysis.

[English Section](#english) | [Polska Sekcja](#polski)

---

<div id="english"></div>

## English Quick Start

### Key Features
*   **SOC/Blue Team:** IOC Extractor, Log Analyzer, User-Agent Parser, Email Headers, JWT Decoder.
*   **Red Team:** GTFOBins Lookup, PowerShell Encoder, RevShell Generator, Critical File Scanner.
*   **Sandbox:** Static binary analysis (PE/ELF), File Hashing (MD5/SHA256), VirusTotal integration.
*   **Automation:** Tool Pipeline (chaining tools) & Plugin System (JSON wrappers for external binaries).

### Install & Run
**Option 1: Binary**
Download from Releases and run the executable. Open http://localhost:8080.

**Option 2: Build from Source (Go 1.21+)**
bash

https://github.com/sanfaro/SecITred_tools/tree/main
go build -ldflags="-s -w" -o SecITRed main.go
./SecITRedAdding Plugins
Create a JSON file in the "plugins" directory (e.g., plugins/ping.json):

json
{
  "name": "ping",
  "category": "recon",
  "command": "ping",
  "args": ["-c", "4", "{{input}}"],
  "inputLabel": "Target IP",
  "needsKey": false
}
<div id="polski"></div>


## POLSKI SZYBKI START

### Glowne Funkcje

*   **SOC/Blue Team:** Ekstrakcja IOC (IP/URL), Analiza Logow i User-Agent, Naglowki Email, Dekoder JWT.
*   **Red Team:** Baza GTFOBins, PowerShell Encoder, Generowanie Reverse Shell, Skaner plikow wrazliwych.
*   **Sandbox:** Statyczna analiza binarna (PE/ELF), Obliczanie Hashy, integracja z VirusTotal.
*   **Automatyzacja:** Pipeline narzedzi (laczenie zadan) i System Pluginow (obsluga zewnetrznych programow przez JSON).

Instalacja
Opcja 1: Binarka
Pobierz z zakladki Releases i uruchom plik wykonywalny. Wejdz na http://localhost:8080.

Opcja 2: Kompilacja (Go 1.21+)

bash
https://github.com/sanfaro/SecITRed](https://github.com/sanfaro/SecITred_tools/tree/main
go build -ldflags="-s -w" -o SecITRed.exe main.go
./SecITRed.exe
Dodawanie Pluginow
Utworz plik JSON w folderze "plugins" (np. plugins/nmap.json):

json
{
  "name": "nmap-scan",
  "category": "recon",
  "command": "nmap",
  "args": ["-F", "{{input}}"],
  "inputLabel": "Adres IP",
  "needsKey": false
}
