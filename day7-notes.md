Network Commands

Fundamental network commands that every Linux administrator needs to know. You'll learn how to test connectivity, download files, check network status, and perform basic firewall operations.

Learn:

- How to test network connectivity using ping and different protocols

- How to download files from the internet using wget and curl

- How to check active network connections and listening ports

- How to view and manipulate basic iptables firewall rules

- How to troubleshoot common network issues on Linux systems


Process Flow

- Connectivity Testing: Use ping to test network reachability

- File Downloads: Download files using wget and curl with various options

- Network Status: Check active connections with netstat and ss

- Firewall Basics: View and add simple iptables rules for network security

**PRACTICE**

==> Test connectivity to Google DNS server

ping 8.8.8.8

==> Download a test file using wget

wget https://httpbin.org/json

==> use curl to fetch and display webpage content

curl https://httpbin.org/ip

==> Download a file with curl and save with specific name

curl -o myip.json https://httpbin.org/ip

==> Check all listening TCP ports

netstat -tlnp

==> Use ss to show listening sockets

ss -tlnp

==> show all active network connections

netstat -tuln

==> check if a specific port is listening

ss -tlnp | grep :22


==> View current iptables rules

sudo iptables -L

==> Add a rule to allow HTTp traffic

sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

==> Test connectivity to a specific port using telent

telnet google.com 80

==> download a file quietly with wget

wget -q https://httpbin.org/json

==> check network interface configuration

ip addr show

==> Test DNS resolution for a domain

nslookup google.com

==> show routing table

ip route show

