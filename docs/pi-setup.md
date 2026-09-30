##Raspberry Pi setup

This node runs Zeek which is used to monitor the mirrored traffic we obtain from our Victim Vm through the use of a NIC that is connected to a NetGear switch that is mirroring the traffic to the Raspberry Pi

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
![Zeek Status](images/zeek-status.png)
### Filebeat Running
![Filebeat Status](images/Filebeat_status.png)
### Filebeat Configuration File
![Filebeat Config](images/filebeat_config.png)
### Zeek Logs
### Zeek Conn log Output
![Connection Logs](images/conn_logs.png)
### Zeek DNS log Output
![DNS Logs](images/DNS_LOGS.png)
### Zeek SSH Log Output
![Zeek SSH Log Output](images/ssh_auth_percentage.png)

