# 🧨 Attack Panel – Hybrid Network Defense Lab

This branch introduces the **Attack Panel**, a set of simulated offensive tools and scripts used to generate malicious traffic in a controlled lab environment. These attacks are designed to test detection and response capabilities of IDS/IPS tools like **Zeek**, **Suricata**, and **Wazuh**.

## 🚩 Purpose

The attack panel simulates common attacker behavior including:
- SSH brute-force attempts
- Network scanning and enumeration
- DNS tunneling
- Malicious file delivery

These scenarios help validate that your **defensive tools** are logging and alerting correctly, and allow you to **test incident response workflows**.


## Visuals

SSH Brute Force using Hydra
![Hydra](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/hydra.png)

DNS Tunneling 
-Use Kali to connect to tunnel 
![DNS_KALI](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/kali_dns_tunnel.png)

-Use Vic VM to create Tunnel and establish connection
![DNS_VM](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/sudo_iodine.png)

-Send file across the tunnel
![DNS_VM](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/scptest.png)

-File made it across to the Kali VM 

![DNS_KALI](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/file_madeit.png)


