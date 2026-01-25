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
[![Platform](https://img.shields.io/badge/platform-%7C%20Linux%20%7C%-lightgrey)](https://github.com/)

**SecITRed** is a comprehensive, standalone cybersecurity hub designed for SOC Analysts, Penetration Testers, and Security Researchers. It acts as a local web server, aggregating essential cryptographic, OSINT, and analysis tools into a single, cohesive interface.

The goal is to eliminate the need for switching between dozens of browser tabs and command-line windows by providing a unified workspace for data decoding, file analysis, and threat intelligence gathering.

---

## 📑 Table of Contents / Spis Treści
1. [🇬🇧 English Documentation](#-english-documentation)
    - [Architecture](#architecture)
    - [Key Features](#key-features)
    - [Installation & Usage](#installation--usage)
    - [Plugin System](#plugin-system)
    - [Binary Inspector (Sandbox)](#binary-inspector-sandbox)
2. [🇵🇱 Polska Dokumentacja](#-polska-dokumentacja)
    - [Architektura](#architektura)
    - [Główne Funkcje](#główne-funkcje)
    - [Instalacja i Użycie](#instalacja-i-użycie)
    - [System Pluginów](#system-pluginów)
    - [Analiza Binarna (Sandbox)](#analiza-binarna-sandbox)

---

<div id="-english-documentation"></div>

## 🇬🇧 English Documentation

### Architecture
SecITRed follows a modular **Client-Server** architecture, packaged into a single executable binary.

*   **Backend (Go):** Handles API requests, performs heavy computations (hashing, binary analysis), manages the plugin system, and interacts with external APIs (VirusTotal, Shodan). It runs a lightweight HTTP server on `localhost:8080`.
*   **Frontend (HTML/JS/CSS):** Served directly from the Go binary using `embed`. It features a responsive UI with tabs for Workspace, Tool Info, Logs, and Pipeline automation.
*   **Communication:** REST API via JSON (`POST /api/run`).

### Key Features

#### 🔵 Blue Team & SOC
*   **IOC Extractor:** Extract and defang/refang IPs, URLs, and emails from raw logs.
*   **User-Agent Parser:** Analyze UA strings to detect bots, scanners, and anomalies.
*   **Log Analyzer:** Pattern matching for common attack vectors (SQLi, XSS, RCE, LFI) in log files.
*   **Email Headers:** Analyze SMTP headers for phishing indicators (SPF/DKIM checks, Relay path).
*   **JWT Decoder:** Inspect JSON Web Tokens without sending data to external sites.

#### 🔴 Red Team & Pentesting
*   **GTFOBins Lookup:** Quick reference for Unix binary privilege escalation (sudo/suid bypass).
*   **PowerShell Encoder:** Convert commands to UTF-16LE Base64 for `powershell -EncodedCommand`.
*   **RevShell Generator:** Generate reverse shell payloads for various languages (Bash, Python, Netcat).
*   **Web Critical Scanner:** Rapidly check for sensitive files (`.env`, `.git`, `robots.txt`) on target URLs.

#### 📦 Binary Analysis Sandbox
A dedicated module for **static analysis** of suspicious files without execution.
*   **File Hashing:** Calculates MD5, SHA1, and SHA256.
*   **VirusTotal Integration:** Automatically queries file hashes against the VT database.
*   **PE/ELF Inspection:** Detects file type, packed sections (UPX), and risky imports (`VirtualAlloc`, `InternetOpen`).
*   **Entropy Check:** Detects encryption or packing based on Shannon entropy.

#### ⚙️ Automation
*   **Pipeline:** Chain multiple tools together (e.g., *Base64 Decode → Extract IPs → Check Shodan*) to automate repetitive tasks.
*   **Plugin System:** Extend capabilities by adding simple JSON files in the `plugins/` directory.

### Installation & Usage

**Option 1: Pre-compiled Binary**
Download the latest release for your OS and run it.

**Option 2: Build from Source**
bash

# Clone the repository
git clone https://github.com/YourUsername/SecITRed.git
cd SecITRed

# Run directly
go run main.go

# Build executable
go build -ldflags="-s -w" -o SecITRed main.go

Running:

Execute the binary: ./SecITRed

Open browser: http://localhost:8080

(Optional) Create a .env file for API keys:

text
VT_API_KEY=your_virustotal_key
SHODAN_API_KEY=your_shodan_key
Plugin System
You can add external tools (Python scripts, system binaries) without recompiling the project.
Create a file plugins/mytool.json:

json
{
  "name": "ping-check",
  "category": "recon",
  "command": "ping",
  "args": ["-c", "4", "{{input}}"],
  "inputLabel": "Target IP",
  "needsKey": false
}
<div id="-polska-dokumentacja"></div>
🇵🇱 Polska Dokumentacja
Architektura
SecITRed opiera się na modułowej architekturze Klient-Serwer, zamkniętej w pojedynczym pliku wykonywalnym.

Backend (Go): Obsługuje żądania API, wykonuje operacje obliczeniowe (hashowanie, analiza binarna), zarządza systemem pluginów oraz komunikuje się z zewnętrznymi API (VirusTotal, Shodan). Działa jako lekki serwer HTTP na porcie 8080.

Frontend (HTML/JS/CSS): Jest "zaszyty" wewnątrz pliku .exe (mechanizm embed). Oferuje responsywny interfejs z zakładkami (Workspace, Pipeline, Logs).

Komunikacja: REST API w formacie JSON (POST /api/run).

Główne Funkcje
🔵 Blue Team & SOC
IOC Extractor: Wyciąganie adresów IP, domen i e-maili z surowych tekstów oraz ich "uzbrajanie/rozbrajanie" (defang/refang).

User-Agent Parser: Analiza nagłówków przeglądarki w celu wykrycia botów, skanerów i anomalii.

Log Analyzer: Wykrywanie sygnatur ataków (SQLi, XSS, RCE, LFI) w plikach logów.

Email Headers: Analiza nagłówków SMTP pod kątem phishingu (weryfikacja ścieżki Relay, SPF/DKIM).

JWT Decoder: Lokalna inspekcja tokenów JWT (bez wysyłania ich do chmury).

🔴 Red Team & Pentesting
GTFOBins Lookup: Szybka baza wiedzy o eskalacji uprawnień przy użyciu binarek systemowych (bypass sudo/suid).

PowerShell Encoder: Kodowanie komend do formatu UTF-16LE Base64 wymaganego przez powershell -EncodedCommand.

RevShell Generator: Generowanie payloadów reverse shell dla różnych języków (Bash, Python, Netcat, PHP).

Web Critical Scanner: Szybki skan URL pod kątem wrażliwych plików (.env, .git, config.php).

📦 Analiza Binarna (Sandbox)
Dedykowany moduł do analizy statycznej podejrzanych plików bez ich uruchamiania.

Hashe Plików: Obliczanie MD5, SHA1 i SHA256.

Integracja VirusTotal: Automatyczne sprawdzanie hashy w bazie VT (wymaga klucza API).

Inspekcja PE/ELF: Rozpoznawanie typu pliku, wykrywanie packerów (UPX) oraz podejrzanych importów funkcji API (VirtualAlloc, InternetOpen).

Analiza Entropii: Wykrywanie szyfrowania lub pakowania kodu na podstawie entropii Shannona.

⚙️ Automatyzacja
Pipeline: Możliwość łączenia narzędzi w łańcuchy (np. Base64 Decode → Wyciągnij IP → Sprawdź w Shodan).

System Pluginów: Możliwość dodawania własnych narzędzi poprzez proste pliki JSON w katalogu plugins/.

Instalacja i Użycie
Opcja 1: Gotowa Binarka
Pobierz najnowszą wersję z zakładki Releases i uruchom ją.

Opcja 2: Kompilacja ze źródeł
Wymagania: Zainstalowane środowisko Go 1.21+.

bash
# Sklonuj repozytorium
git clone https://github.com/TwojNick/SecITRed.git
cd SecITRed

# Uruchom bezpośrednio
go run main.go

# Zbuduj plik wykonywalny
go build -ldflags="-s -w" -o SecITRed.exe main.go
Uruchomienie:

Włącz plik wykonywalny: ./SecITRed.exe

Otwórz przeglądarkę: http://localhost:8080

(Opcjonalnie) Skonfiguruj klucze API w zmiennych środowiskowych:

VT_API_KEY – dla VirusTotal

SHODAN_API_KEY – dla Shodan

System Pluginów
Możesz dodać zewnętrzne narzędzia (skrypty Python, binarki systemowe) bez rekompilacji projektu.
Utwórz plik plugins/moj_skrypt.json:

json
{
  "name": "szybki-skan",
  "category": "recon",
  "command": "nmap",
  "args": ["-F", "{{input}}"],
  "inputLabel": "Adres IP",
  "needsKey": false
}
