# asterisk_exporter
The Asterisk Exporter is a lightweight and efficient Prometheus exporter designed specifically for monitoring Asterisk PBX systems. It exposes various metrics related to Asterisk, such as channels, peers, uptime, and more, allowing you to gain insights into the performance and health of your Asterisk infrastructure.

# How to use
1. Download the latest binary release
2. Copy this binary to /usr/local/bin
3. Get your peers' names using the command asterisk -rvx "sip show peers"
4. create file trunk_names.txt
5. put sip name from step-3 to trunk_names.txt
6. Copy the asterisk_exporter.service file to the /etc/systemd/system/ directory
7. systemctl start asterisk_exporter
8. systemctl enable asterisk_exporter
9. Add config to prometheus.yml file:
```
scrape_configs:
  - job_name: 'asterisk_exporter'
    static_configs:
      - targets:
          - asterisk_server_ip:9110
        labels:
          hostname: asterisk_server_hostname
    scrape_interval: 15s
    scrape_timeout: 10s
```
9. import dashboard.json in grafana 

   
   
