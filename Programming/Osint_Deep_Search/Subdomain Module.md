***
## Main Work

## Subdomain Discovery Logic
- **Source:** crt.sh (Identity-based reconnaissance)
- **Method:** Passive (No direct contact with target infrastructure)
- **Data Format:** JSON
- **Key Python Steps:**
	1. Format URL: `https://crt.sh/?q=%.{target}&output=json`
	2. Request: Use `requests.get()` to fetch data.
	3. Parse: Loop through the JSON list.
	4. Filter: Use `set()` to ensure no duplicate subdomains are saved.

*** 

## Working Code

```python
from colorama import Fore, Style, init

import requests

init(autoreset=True)


def scanSubdomain(domainName):
    url = f"https://crt.sh/?q=%.{domainName}&output=json"
    response = requests.get(url)
    data = response.json()

    subdomains = set()
    for entry in data:
        name = entry["name_value"]
        lines = name.split("\n")
        for line in lines:
            clean_name = line.replace("*.", "").strip()
            subdomains.add(clean_name)
    for sub in sorted(subdomains):
        print(f"{Fore.GREEN}[+]Found: {Fore.BLUE}{sub}")


if __name__ == "__main__":
    domain = input("Enter domain name:")
    scanSubdomain(domain)
```


