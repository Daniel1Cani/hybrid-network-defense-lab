# Hybrid Network Defense Lab (IDS + SIEM)

A home security-monitoring lab. A **Raspberry Pi** watches mirrored switch traffic with **Zeek**, ships the logs with **Filebeat** to an **ELK** stack on an Ubuntu VM, and **Kibana** dashboards show attacks launched from a Kali VM. The pipeline processed 2,000+ SSH events with a 99% detection rate.

## Architecture

```
  Kali VM (attacker) ──┐
                       ├──▶ Netgear switch ──mirror port──▶ Raspberry Pi (Zeek 6.0.4 + Filebeat 7.10.2)
  Victim VM ───────────┘                                          │ JSON logs over Beats (5044)
                                                                  ▼
                                      Ubuntu VM (SOC): Logstash ─▶ Elasticsearch ─▶ Kibana
```

| Component | Role |
|---|---|
| Raspberry Pi | Zeek inspects mirrored traffic (conn, DNS, HTTP, SSH logs); Filebeat forwards them |
| Ubuntu VM (SOC) | Logstash parses and enriches, Elasticsearch indexes, Kibana visualizes |
| Victim VM | Generates normal and attack-target traffic |
| Kali VM | Runs the attacks |
| Netgear switch | Mirrors traffic to the Pi |

## What it detects

| Attack | Tool | What shows up |
|---|---|---|
| SSH brute force | Hydra | Spike of failed SSH auths by source ([SSH charts](docs/soc-setup.md)) |
| Port scanning | Nmap | Many failed connections (S0 events) per source and port |
| DNS tunneling | iodine | Unusual DNS volume and NXDOMAIN patterns |

Kibana dashboards cover DNS requests, NXDOMAIN detection, HTTP URIs, SSH attempts, and failed connections by source and protocol.

## Docs

- [Raspberry Pi setup](docs/pi-setup.md): Zeek and Filebeat
- [SOC VM setup](docs/soc-setup.md): Logstash, Elasticsearch, Kibana
- [Attack scenarios](docs/attacks.md): Hydra, DNS tunnel, Nmap, with screenshots

## Skills shown

Network traffic analysis, IDS deployment, log pipelines (Beats, Logstash, Elasticsearch), detection dashboards, and attack simulation to validate detections.

## Author

Daniel Cani, [LinkedIn](https://www.linkedin.com/in/danielcani) · MIT License
