# asterisk_exporter
The Asterisk Exporter is a lightweight and efficient Prometheus exporter designed specifically for monitoring Asterisk PBX systems. It exposes various metrics related to Asterisk, such as channels, peers, uptime, and more, allowing you to gain insights into the performance and health of your Asterisk infrastructure.

# How to use
1. Download the latest binary release
2. Copy this binary to /usr/local/bin
3. Get your peers' names using the command asterisk -rvx "sip show peers"
4. Copy the asterisk_exporter.service file to the /etc/systemd/system/ directory
5. In the service file, change the peer's name with your actual peer's name (output of step 3)
   Modify this line in the service file: ExecStart=/usr/local/bin/asterisk_exporter_amd64 -port 9110 -filter "peername"
   If you have multiple peers, use: ExecStart=/usr/local/bin/asterisk_exporter_amd64 -port 9110 -filter "peername1|peername2|peername3"
6. systemctl start asterisk_exporter
7. systemctl enable asterisk_exporter
8. Add config to prometheus.yml file:
```
scrape_configs:
  - job_name: 'UP112DR asterisk'
    static_configs:

      - targets:
          - 137.59.52.140:9110
        labels:
          hostname: v140tataindore
 
    relabel_configs:
      - source_labels: [__address__]
        regex: '(.+):\d+'
        target_label: instance
        replacement: '$1'


    scrape_interval: 7s
    scrape_timeout: 6s
```
 

   
   
