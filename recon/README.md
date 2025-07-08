# Recon – Reconnaissance Tools & Techniques

> The first phase of every successful cyber attack — **know your target better than they know themselves**.

This folder is a curated collection of tools, scripts, and methodologies I personally use to perform deep reconnaissance on web applications, organizations, infrastructure, and individuals.

Recon is not just about running a few tools — it's about building a detailed map of the attack surface, identifying weak entry points, and laying the foundation for successful exploitation. I treat recon like **digital stalking with purpose** — a combination of automation, creativity, and obsession.

---

##  Goals of Recon

- Discover subdomains & IPs
- Identify tech stack (WAFs, CMS, CDN, etc.)
- Fingerprint services & software versions
- Enumerate open ports and services
- Collect endpoints, secrets, and files
- Map organization structure (emails, employees)
- Passively and actively expand the attack surface

---

## Contents

| Tool / Script | Description |
|---------------|-------------|
| `subdomain_enum.sh` | My custom bash automation using Amass, Subfinder, Assetfinder, and crt.sh |
| `passive_recon.py` | Passive recon with sources like Wayback, GitHub, CommonCrawl, AlienVault |
| `port_scanner.py` | Fast scanning using Masscan and Nmap |
| `asn_lookup.sh` | ASN to IP range extraction, useful for mapping infra of large companies |
| `dns_brute.sh` | Wordlist-based DNS brute-forcing |
| `screenshotter.py` | Headless browser to screenshot large numbers of URLs for visual inspection |
| `tls_fingerprint.py` | Detects TLS cert info, expiry, and misconfigurations |
| `js_parser.py` | Extract endpoints, secrets, and APIs from JavaScript files |
| `tech_stack_fingerprinter.py` | Uses Wappalyzer API + manual curl headers to detect tech stack |

---

## Recon Methodology

Here’s how I typically perform recon in real engagements and bug bounties:

1. **Subdomain Enumeration**  
   - Tools: `Amass`, `Subfinder`, `Assetfinder`, `crt.sh`, `dnsdumpster`
   - Goal: Discover all possible subdomains, even forgotten staging/dev domains.

2. **IP & ASN Mapping**  
   - ASN lookup from public IPs to identify owned infra.
   - Pull netblocks from ARIN, RIPE, etc.

3. **DNS Recon**  
   - Brute-force subdomains with wordlists.
   - Resolve wildcard DNS.

4. **Port Scanning**  
   - Use `Masscan` for wide-range scanning, then `Nmap` for version detection.

5. **Web Probing**  
   - Tools: `httpx`, `httprobe`, `waybackurls`
   - Collect all live domains and accessible URLs.

6. **Content Discovery**  
   - Use `ffuf`/`dirsearch` for hidden paths.
   - Look for `robots.txt`, `.git`, `.env`, `sitemap.xml`.

7. **Fingerprinting**  
   - Identify CMS, frameworks, plugins.
   - Capture TLS info, response headers, favicon hashes.

8. **JS Analysis**  
   - Pull JavaScript files.
   - Extract endpoints, keys, and internal APIs using `LinkFinder` and regex.

9. **Visual Recon**  
   - Take screenshots of all discovered assets.
   - Prioritize targets with login panels, admin paths, etc.

10. **Data Correlation**  
    - Merge outputs, de-duplicate, and rank based on exposure and value.

---

##  Tips for Deep Recon

- Always go beyond tools. Inspect raw output manually.
- Focus on assets *not meant to be public* — dev/test sites, forgotten subdomains, exposed APIs.
- Monitor newly registered domains for your target company.
- Use AI to analyze JavaScript logic and extract hidden secrets.
- Loop through tools — new subdomains = new endpoints = new recon.

---
## Learning Resources

- [NahamSec Recon Workflow](https://youtu.be/bJPI3Q3Hpf0)
- [TomNomNom Tools](https://github.com/tomnomnom) — `assetfinder`, `httprobe`, `waybackurls`
- [Project Discovery Toolkit](https://projectdiscovery.io)
- [Recon Handbook by STÖK](https://github.com/stok/sec-tools/blob/main/recon-handbook.md)
- [@thecybermentor Bug Bounty Recon Series](https://www.youtube.com/@TheCyberMentor)
- [PayloadAllTheThings - Recon Section](https://github.com/swisskyrepo/PayloadsAllTheThings#reconnaissance)
