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
pi@raspberrypi:~ $ sudo zeekctl status
Name         Type       Host          Status    Pid    Started
zeek         standalone localhost     running   3787   01 Jun 21:51:34

### Filebeat Running
![Filebeat Status](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/Filebeat_status.png)
pi@raspberrypi:~ $ ps aux | grep filebeat
root         774  0.5  0.9 1537136 79072 ?       Ssl  Jun01   0:55 /home/pi/filebeat-7.10.2-linux-arm64/filebeat -c /home/pi/filebeat.yml
pi          8302  0.0  0.0   6240  1616 pts/0    S+   00:00   0:00 grep --color=auto filebeat### Filebeat Configuration
![Filebeat Config](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/filebeat_config.png)


### Zeek Logs
### Zeek conn.log Output
![Connection Logs](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/conn_logs.png)
pi@raspberrypi:~ $ sudo tail -f /usr/local/zeek/logs/current/conn.log
{"ts":1748836778.974758,"uid":"CLbznn1ONrodLZepJ5","id.orig_h":"fe80::f669:42ff:fe5d:1a4","id.orig_p":135,"id.resp_h":"ff02::1:ff2a:59a0","id.resp_p":136,"proto":"icmp","duration":12.028352975845337,"orig_bytes":288,"resp_bytes":0,"conn_state":"OTH","local_orig":true,"local_resp":false,"missed_bytes":0,"orig_pkts":12,"orig_ip_bytes":864,"resp_pkts":0,"resp_ip_bytes":0}

### Zeek dns.log Output
![DNS Logs](https://raw.githubusercontent.com/Daniel1Cani/hybrid-network-defense-lab/screenshots/DNS_LOGS.png)
pi@raspberrypi:~ $ sudo tail -f /usr/local/zeek/logs/current/dns.log
{"ts":1748836858.956996,"uid":"C0G6Ze4drqB7d7Hdi6","id.orig_h":"fe80::ad87:a111:cb60:34f5","id.orig_p":5353,"id.resp_h":"ff02::fb","id.resp_p":5353,"proto":"udp","trans_id":0,"query":"desktop-8vttdtl._dosvc._tcp.local","qclass":1,"qclass_name":"C_INTERNET","qtype":255,"qtype_name":"*","rcode":0,"rcode_name":"NOERROR","AA":true,"TC":false,"RD":false,"RA":false,"Z":0,"answers":["desktop-8vttdtl._dosvc._tcp.local"],"TTLs":[0.0],"rejected":false}
