# 🛡️ OPNsense Homelab Firewall + VLAN Segmentation

This project documents my personal homelab using OPNsense to implement firewall rules, VLAN isolation, and basic intrusion detection using Suricata. I use this lab to simulate a real network environment and practice cybersecurity skills.

---

## 🔧 Lab Overview

**Hardware:**
- Unraid NAS - 192.168.1.12
- Desktop PC (Windows 11) - 192.168.1.10
- Omada EAP650 AP
- Cisco switch
- TP-Link Switch
- OPNsense router (self-built)

**VLANs:**
| VLAN | Purpose           | Subnet           |
|------|-------------------|------------------|
| 10   | Main LAN          | 192.168.10.0/24  |
| 20   | Docker            | 192.168.20.0/24  |
| 30   | Guest Wi-Fi       | 192.168.30.0/24  |

---

## 🔐 Firewall Rules

All VLANs are isolated from each other using deny-all rules. Only specific ports/services are allowed through the firewall.

- 🔒 Block all inter-VLAN traffic
- 🌐 Allow LAN → WAN for all
- 📥 Allow specific ports from VLAN 10 → VLAN 20 (e.g. for admin access)

See `firewall-configs/rules.txt` for full ruleset.

---

## 🧪 Intrusion Detection with Suricata

Suricata is running on the WAN interface. I've tuned the ruleset to alert on:

- Port scans
- SSH brute-force attempts
- Suspicious DNS queries

Sample alerts are stored in `logs/suricata-alerts.log`.

---

## 🖼️ Network Diagram

<img src="diagrams/homelab-network.png" alt="Homelab Diagram" width="600"/>

---

## 📜 Lessons Learned

- OPNsense + Suricata is easy to deploy but takes time to tune.
- VLANs are crucial for home security and keeping Docker containers isolated.
- Creating firewall rules manually forces you to understand real-world networking.

---

## 🚧 Future Plans

- Add Wazuh for full SIEM stack
- Automate log parsing with Python
- Expand ruleset for malware detection

---

## 📂 File Structure

