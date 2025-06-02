##Raspberry Pi setup

This node runs Zeek which is used to monitor the mirrored traffic we obtain from our Victeim Vm through the use of a NIC that is connected to a NetGear switch that is mirroring the traffic to the Raspberry Pi

### Services in Use 
-Zeek 6.0.4

-Filebeat OSS.7.10.2

```

               ┌────────────┐
               │  Internet  │
               └────┬───────┘
                    │
              ┌─────▼──────┐
              │ Netgear SW │
              └────┬───────┘
         Mirror    │
         Port      │
        ▼          ▼
┌──────────────┐ ┌──────────────┐
│ Raspberry Pi │ │  Victim VM   │
│ (Zeek, FB)   │ │ (Logs Gen.)  │
└──────┬───────┘ └──────────────┘
       │
       ▼
┌──────────────────────┐
│   Ubuntu VM (SOC)    │
│ ┌──────────────────┐ │
│ │ Logstash + Kibana│ │
│ └──────────────────┘ │
│ ┌──────────────────┐ │
│ │  Elasticsearch   │ │
│ └──────────────────┘ │
└──────────────────────┘
```

### Run Commands
### Zeek Running
![Zeek Status](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/zeek-status.png)

### Filebeat Running
![Filebeat Status](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/Filebeat_status.png)

###Filebeat Configuration File

![Filebeat Config](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/filebeat_config.png)


### Zeek Logs
### Zeek conn.log Output
![Connection Logs](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/conn_logs.png)


### Zeek dns.log Output
![DNS Logs](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/DNS_LOGS.png)

