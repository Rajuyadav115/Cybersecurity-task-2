# Firewall Notes — Task 2

## Objective

Demonstrate basic iptables rules, and show that they actually stop a scan.

## 1. Simple Allow/Deny Rules

View current rules:
```bash
sudo iptables -L -v -n
```

Allow SSH (22) and HTTP (80), drop everything else inbound by default:
```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -P INPUT DROP
```

Deny one specific port (e.g. block Telnet, port 23):
```bash
sudo iptables -A INPUT -p tcp --dport 23 -j DROP
```

Persist the rules so they survive a reboot:
```bash
sudo iptables-save > /etc/iptables/rules.v4
```

`[ ]` Screenshot of `iptables -L -v -n` before and after adding rules.

## 2. Blocking a Port Scan — Before/After Demo

1. From Kali, run a baseline scan against the target *before* adding any rule:
   ```bash
   nmap -sS <target-ip>
   ```
   `[ ]` Note which ports show `open`.

2. On the target, add a DROP rule for one of those ports (e.g. 23):
   ```bash
   sudo iptables -A INPUT -p tcp --dport 23 -j DROP
   ```

3. Re-run the identical scan from Kali:
   ```bash
   nmap -sS <target-ip>
   ```
   `[ ]` Note that the port now shows `filtered` instead of `open` — this is your evidence the rule works.

## Summary

`[ ]` 2–3 sentences on what changed between the "before" and "after" scan, and why a production firewall config would need more than just this one rule.
