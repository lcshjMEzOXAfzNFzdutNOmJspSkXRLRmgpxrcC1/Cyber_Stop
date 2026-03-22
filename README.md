# ☠ CyberStop — Multi-Tool for Cybersecurity Professionals

```
 ██████╗██╗   ██╗██████╗ ███████╗██████╗ ███████╗████████╗ ██████╗ ██████╗
██╔════╝╚██╗ ██╔╝██╔══██╗██╔════╝██╔══██╗██╔════╝╚══██╔══╝██╔═══██╗██╔══██╗
██║      ╚████╔╝ ██████╔╝█████╗  ██████╔╝███████╗   ██║   ██║   ██║██████╔╝
██║       ╚██╔╝  ██╔══██╗██╔══╝  ██╔══██╗╚════██║   ██║   ██║   ██║██╔═══╝
╚██████╗   ██║   ██████╔╝███████╗██║  ██║███████║   ██║   ╚██████╔╝██║
 ╚═════╝   ╚═╝   ╚═════╝ ╚══════╝╚═╝  ╚═╝╚══════╝   ╚═╝    ╚═════╝ ╚═╝
                     ☠  REAP WHAT THEY HIDE  ☠
```

> **For authorized testing and educational use only.**  
> Unauthorized use is illegal and unethical.

---

## Overview

CyberStop is a Python-based, terminal-driven multi-tool for cybersecurity professionals and ethical hackers. It features a modular plugin system, a grim reaper ASCII art banner, and covers a comprehensive range of security research tasks — from OSINT and network scanning to password tools and forensics.

---

## Features

### 🧠 OSINT / Reconnaissance
| Module | Description |
|--------|-------------|
| IP Geolocation | Country, city, ISP, ASN, coordinates via ip-api.com |
| Username Search | Probe 30+ platforms (GitHub, Twitter, Instagram, etc.) |
| Email Breach Check | Check HaveIBeenPwned for data breaches |
| Phone Lookup | Carrier, region, country code detection |
| Domain WHOIS | Registrar, creation/expiry, nameservers |
| DNS Enumeration | A, AAAA, MX, NS, TXT, DMARC, DKIM records |
| Subdomain Enumeration | crt.sh + wordlist brute-force |
| Wayback Machine URLs | Historical URL archive retrieval |
| Dox Tool | Combined OSINT meta-module with ethics warning |

### 🌐 Network / Infrastructure
| Module | Description |
|--------|-------------|
| Port Scanner | Multi-threaded TCP scan on custom port ranges |
| Ping Sweep | ICMP host discovery for subnets |
| Traceroute | Path tracing + per-hop geolocation |
| HTTP Headers | Security header analysis and missing header detection |
| SSL/TLS Analyzer | Certificate chain, expiry, SANs, cipher suites |
| ASN Lookup | Autonomous System Number and IP prefix data |

### 🌍 Web Application Testing
| Module | Description |
|--------|-------------|
| CMS Fingerprinting | Detect WordPress, Joomla, Drupal, Shopify, etc. |
| WAF Detection | Identify Cloudflare, AWS WAF, Akamai, Imperva, etc. |
| Git / Secrets Finder | Check for exposed .git, .env, config files |

### 🔑 Password & Crypto Tools
| Module | Description |
|--------|-------------|
| Password Generator | Custom charset, length, entropy estimation |
| Hash Generator | MD5, SHA1, SHA256, SHA512, SHA3, bcrypt |
| Encoding Toolkit | Base64, Base32, Hex, ROT13, URL, Binary, HTML |
| XOR Cipher | XOR encryption/decryption with user key |
| Password Strength | Entropy, complexity checks, common password detection |

### 🔍 Malware / Forensics
| Module | Description |
|--------|-------------|
| File Hasher | MD5, SHA1, SHA256, SHA512 + hash verification |
| Exif Extractor | GPS, camera model, software from images |
| Strings Extractor | ASCII/Unicode strings from binary files |

### 🛠️ Utility / Productivity
| Module | Description |
|--------|-------------|
| Wordlist Generator | Permutations, leetspeak, number appends, combos |
| Payload Encoder | Base64, URL, Hex, HTML Entity, PowerShell B64 |
| Reverse Shell Generator | Bash, Python, Netcat, PHP, Ruby, PowerShell, Perl |
| Base Converter | Binary ↔ Decimal ↔ Hex ↔ Octal |
| Report Saver | View and manage saved module outputs |

---

## Installation

### Requirements
- Python 3.8 or higher
- pip

### Quick Start

```bash
# 1. Clone or download this folder
cd CYBER_STOP

# 2. (Recommended) Create a virtual environment
python3 -m venv venv
source venv/bin/activate      # Linux/macOS
venv\Scripts\activate.bat     # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run CyberStop
python3 cyberstop.py
```

---

## Project Structure

```
CYBER_STOP/
├── cyberstop.py          # Main launcher with reaper banner + menu
├── requirements.txt      # Python dependencies
├── README.md             # This file
├── modules/              # Plugin modules (each is self-contained)
│   ├── __init__.py
│   ├── ip_geo.py         # IP Geolocation
│   ├── username_search.py
│   ├── email_breach.py
│   ├── phone_lookup.py
│   ├── domain_whois.py
│   ├── dns_enum.py
│   ├── subdomain_enum.py
│   ├── wayback_urls.py
│   ├── port_scan.py
│   ├── ping_sweep.py
│   ├── traceroute_tool.py
│   ├── http_headers.py
│   ├── ssl_analyzer.py
│   ├── asn_lookup.py
│   ├── cms_fingerprint.py
│   ├── waf_detect.py
│   ├── git_finder.py
│   ├── password_gen.py
│   ├── hash_gen.py
│   ├── base64_tool.py
│   ├── xor_cipher.py
│   ├── password_strength.py
│   ├── file_hasher.py
│   ├── exif_extractor.py
│   ├── strings_extractor.py
│   ├── wordlist_gen.py
│   ├── payload_encoder.py
│   ├── reverse_shell_gen.py
│   ├── base_converter.py
│   ├── dox_tool.py       # Combined OSINT meta-module
│   └── report_saver.py
├── utils/                # Shared utilities
│   ├── __init__.py
│   ├── colors.py         # ANSI color codes and helpers
│   └── helpers.py        # Common functions (save, clipboard, validate, HTTP)
└── reports/              # Auto-created on first save
    └── (your saved reports go here)
```

---

## Adding Custom Modules

CyberStop uses a plugin system. To add a new module:

1. Create a new `.py` file in `modules/`
2. Follow the template:

```python
name = "My Custom Module"

def run():
    from utils.colors import banner, success, error, CYAN
    from utils.helpers import get_input, prompt_save

    banner("MY CUSTOM MODULE", CYAN)
    
    target = get_input("Enter target")
    if target is None:
        return
    
    # ... your logic here ...
    
    output = "results go here"
    prompt_save(output, "my_module")
```

3. Add the module filename (without `.py`) to `MODULE_CATEGORIES` in `cyberstop.py`

That's it — the launcher auto-discovers and loads it.

---

## Output / Reports

All module outputs can be saved to the `reports/` directory:
- Plain text `.txt`
- JSON `.json`
- CSV `.csv`
- HTML `.html`

Use the **Report Saver** module to browse and manage saved reports.

---

## Debug Mode

Run with `CYBERSTOP_DEBUG=1` to see full tracebacks on module errors:

```bash
CYBERSTOP_DEBUG=1 python3 cyberstop.py
```

---

## Optional API Keys

Some modules work better with API keys (not required for basic use):

| Service | Module | Get Key |
|---------|--------|---------|
| HaveIBeenPwned | Email Breach | https://haveibeenpwned.com/API/v3 |
| Shodan | (planned) | https://shodan.io |
| Censys | (planned) | https://censys.io |
| VirusTotal | (planned) | https://virustotal.com |

---

## Legal Disclaimer

> This tool is intended for **authorized security testing, CTF challenges, penetration testing with written permission, and educational research only.**
>
> The authors and contributors are **not responsible** for any misuse of this software. Using CyberStop against targets without explicit written authorization may violate the Computer Fraud and Abuse Act (CFAA), Computer Misuse Act (UK), GDPR, and other applicable laws.
>
> **You are solely responsible for your actions.**

---

## License

Apache License 2.0 — see individual module files for attribution.

---

*Built with ☠ and Python. Stay legal, stay ethical.*
