### Ubuntu VM (SOC) Setup'

This nodes serves as the SOC, aggregating and analyzing log data that is coming from the Raspberry Pi monitoring node. It gets the zeek logs via Filebeat and then uses Logstash on the SOC VM to parse, transform and route data into Elasticsearch which is then visualized with Kibana

### Services in use
ELK-

ElasticSearch

Logstash 

Kibana

### Architecture 
              +-------------------+
              |    Raspberry Pi   |
              |  (Zeek + Filebeat)|
              +---------+---------+
                        |
                        | JSON logs over Beats (5044)
                        v
              +---------+---------+
              |      Logstash     |
              +---------+---------+
                        |
                        v
              +---------+---------+
              |   Elasticsearch   |
              +---------+---------+
                        |
                        v
              +---------+---------+
              |      Kibana       |
              +-------------------+

### Visuals 
Logstash status
![Logstash_status](images/logstash_status.png)

Elasticsearch status
![Elasticsearch_status](images/elasticsearch_status.png)

DNS Logs Visualization
![DNS](images/DNS_requests.png)

SSH Attempts
![SSH](images/ssh_chart.png)

SSH Authentication Attemps
![SSH](images/ssh_auth_percentage.png)

HTTP requests
![HTTP](images/http_uri.png)

NXDomain Detection
![DOMAIN](images/NXDOMAINDetetction.png)

