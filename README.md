# asterisk_exporter
The Asterisk Exporter is a lightweight and efficient Prometheus exporter designed specifically for monitoring Asterisk PBX systems. It exposes various metrics related to Asterisk, such as channels, peers, uptime, and more, allowing you to gain insights into the performance and health of your Asterisk infrastructure.

# How to use
1. Download latest binary release 
2. copy this binary to /usr/local/bin
3. get your peers name using asterisk -rvx "sip show peers"
4. copy asterisk_exporter.service file in /etc/systemd/system/ directory
5. in service file change peer's name with your actual peer's name (output of step 3)
   change in this line in service file ==> ExecStart=/usr/local/bin/asterisk_exporter_amd64 -port 9110 -filter "peername"
   if you have multiple peers then use  ==> ExecStart=/usr/local/bin/asterisk_exporter_amd64 -port 9110 -filter "peername1|peername2|peername3"
6. systemctl start asterisk_exporter
7. systemctl enable asterisk_exporter

   
   
