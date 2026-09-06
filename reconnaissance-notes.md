# Reconnaissance Notes — Task 2

**Target:** Metasploitable2 VM — `<target-ip>` (find yours inside the VM with `ip a`, or check the VirtualBox Host-Only range — usually `192.168.56.0/24`)

## 1. Passive Reconnaissance

Passive recon gathers information *without* touching the target directly.

### Whois
```bash
whois <domain-or-ip>
```
`[ ]` Paste your output / summary here — registrar, netblock owner, contact info.

### Nslookup / DNS
```bash
nslookup <domain>
dig <domain> ANY
```
`[ ]` Record the A / MX / NS records returned.

### Google Dorking
Search operators for OSINT practice — only ever run these against domains you own or are authorized to test:
```
site:target.com filetype:pdf
site:target.com intitle:"index of"
site:target.com inurl:admin
```
`[ ]` Note anything indexed that shouldn't be public (staging pages, exposed directories, leaked docs).

### Shodan
```
net:<your-ip-range>
hostname:<domain>
```
`[ ]` Note exposed services Shodan reports. Since this lab runs on an isolated Host-Only network, this will likely just be "N/A — not internet-facing," which is itself worth stating.

## 2. Active Reconnaissance

### Ping Sweep
```bash
nmap -sn 192.168.56.0/24
```
`[ ]` Paste the list of live hosts discovered.

### Banner Grabbing
```bash
nc -nv <target-ip> 21    # FTP
nc -nv <target-ip> 22    # SSH
nc -nv <target-ip> 80    # HTTP
telnet <target-ip> 25    # SMTP
```
`[ ]` Record the service banners returned — version strings here are what you'll cross-reference against CVEs later in `nmap-analysis.md` and `vulnerability-report.pdf`.

## Summary

`[ ]` 2–3 sentences: what did recon tell you about the attack surface before you even ran a full port scan?
