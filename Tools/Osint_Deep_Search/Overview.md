# Project: OSINT Deep Scraper (Python)

> [!info] Project Goal To build a modular reconnaissance tool that automates the collection of subdomains, DNS records, and metadata to map a target's attack surface.

## 🛠️ Tech Stack & Libraries

For a pentesting tool, these libraries provide the best balance of speed and depth:

| Library         | Function                                   | Installation                 |
| --------------- | ------------------------------------------ | ---------------------------- |
| `requests`      | API communication (crt.sh, HaveIBeenPwned) | `pip install requests`       |
| `dns.resolver`  | DNS Enumeration (MX, TXT, A records)       | `pip install dnspython`      |
| `BeautifulSoup` | Scraping emails and links from HTML        | `pip install beautifulsoup4` |
| `asyncio`       | Asynchronous execution (high speed)        | Built-in                     |
| `colorama`      | Red/Green terminal output for status       | `pip install colorama`       |
| `shodan`        | IoT/Service search (API required)          | `pip install shodan`         |

## 🏗️ Architecture Overview

The tool follows a **Modular Design**. Each "Module" handles one specific OSINT task.

### 1. Subdomain Module (`subdomains.py`)

- **Action:** Sends a request to `https://crt.sh/?q=%.example.com&output=json`.
    
- **Logic:** Parses the JSON response and uses a `set()` to remove duplicate subdomains.
    
- **Goal:** Find "forgotten" development or staging servers.
    

### 2. DNS Recon Module (`dns_recon.py`)

- **Action:** Uses `dns.resolver` to query the target domain.
    
- **Logic:** Looks for `TXT` records (often contain API keys or verification tokens) and `MX` records (identifies mail providers like Outlook or Gmail).
    

### 3. Metadata Module (`metadata.py`)

- **Action:** Scrapes the target site for files (`.pdf`, `.docx`, `.xls`).
    
- **Logic:** Downloads them temporarily and uses a library like `exiftool` to find usernames or software versions hidden in the file properties.
    

---

## 🚀 Working Logic (Pseudo-code)

This is how your `main.py` should orchestrate the modules:

Python

```
import asyncio
from modules import subdomains, dns_recon, scanner

async def start_recon(target):
    print(f"[*] Starting OSINT on: {target}")
    
    # 1. Passive Discovery (No packets sent to target)
    subs = await subdomains.fetch(target)
    
    # 2. Infrastructure Check
    records = dns_recon.get_all(target)
    
    # 3. Report Generation
    save_to_obsidian(target, subs, records)

if __name__ == "__main__":
    target_domain = input("Target Domain: ")
    asyncio.run(start_recon(target_domain))
```

---

## 📝 Integration with Obsidian

Since you are a notes-taker, have your Python script save its final report as a `.md` file directly in your vault.

- **Automated Template:** Have the script write `# Recon Report: {{domain}}` at the top.
    
- **Tagging:** Use `f.write("#target #recon #pending")` so you can find the results easily using the Obsidian search.