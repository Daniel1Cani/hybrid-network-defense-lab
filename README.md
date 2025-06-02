# Hybrid Network Defense Lab

This project simulates a real-world network security monitoring environment using a hybrid physical-virtual architecture. It integrates **Zeek**,**Filebeat**, **Logstash**, **Elasticsearch**, and **Kibana** to build a functional IDS pipeline with SIEM capabilities.

The lab is split between a **Raspberry Pi monitoring node** and a **Ubuntu VM-based Security Operations Center (SOC)**, communicating via a mirrored network switch to collect and analyze traffic from a victim machine.

---

## 🔧 Project Structure

| Component       | Role                                                                 |
|----------------|----------------------------------------------------------------------|
| 🖥️ Ubuntu VM (SOC) | Runs Logstash, Elasticsearch, and Kibana for parsing and visualization |
| 🍓 Raspberry Pi   | Runs Zeek + Filebeat to monitor mirrored traffic from the switch    |
| 🧪 Victim VM      | Generates attack/test traffic                                        |
| 🔄 Netgear Switch | Mirrors traffic to the Pi for packet inspection                     |

---

## 📂 Documentation

- [`pi-setup`](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/pi-setup)  
  Setup instructions and configurations for the Raspberry Pi (Zeek + Filebeat)

- [`Ubuntu-VM-(SOC)-setup`](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/Ubuntu-VM-(SOC)-setup)  
  Configuration for Logstash pipelines, Elasticsearch, and Kibana dashboards

- [`screenshots`](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/screenshots)  
  Visual evidence and dashboard captures demonstrating detection success

---

## 📊 Features Demonstrated

- ✅ **Zeek** packet inspection for DNS, HTTP, SSH logs
- ✅ **Logstash pipelines** for JSON log parsing and enrichment
- ✅ **Kibana visualizations** for brute-force attacks, DNS anomalies, failed connections
- ✅ **Live data flow** from physical switch mirror port to SIEM stack
- ✅ **ELK Stack integration** for scalable log indexing and querying

---

## 🚀 Getting Started

> Want to try this setup? Begin with:
1. [Pi Setup Guide](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/pi-setup)
2. [SOC VM Setup](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/Ubuntu-VM-(SOC)-setup)
3. View results under the [Screenshots](https://github.com/Daniel1Cani/hybrid-network-defense-lab/tree/screenshots) branch

---

## 👤 Author

**Daniel Cani**  
Cybersecurity Student & Network Security Enthusiast  
[LinkedIn](https://www.linkedin.com/) *(Insert your link)* | [Portfolio](https://yourportfolio.site) *(Optional)*

---

## 📄 License

This project is licensed under the MIT License.

