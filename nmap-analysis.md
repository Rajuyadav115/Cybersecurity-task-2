# Nmap Scan Analysis — Task 2

Source data: `nmap_report.txt` (scanned against Metasploitable2, isolated lab network)

## Open Ports & Services

| Port | Protocol | Service | Version (from `-sV`) | Notes |
|---|---|---|---|---|
| 21 | TCP | FTP | `[ ]` | |
| 22 | TCP | SSH | `[ ]` | |
| 23 | TCP | Telnet | `[ ]` | |
| 80 | TCP | HTTP | `[ ]` | |
| `[ ]` | | | | |

`[ ]` Fill this in from your actual `-sV` output — Metasploitable2 typically exposes 15–20+ services, so expect more rows than shown here.

## OS Detection Result

`[ ]` What did `-O` report, and how confident was Nmap (the % match it gives)?

## Risk Observations

For each open/interesting port, note *why* it matters — don't just list it:

- **Port `[ ]` — `[service]`**: `[ ]` why this is risky (e.g. outdated version with known CVEs, cleartext protocol, default creds likely)

## Attack Surface Summary

`[ ]` 3–5 sentences: given everything found, which 2–3 services would you prioritize attacking first in Task 3/4, and why?

## Next Steps

This analysis feeds directly into:
- `vulnerability-report.pdf` — formal severity-rated findings from OpenVAS
- Task 4 exploitation (Metasploit, targeting whichever service looks weakest here)
