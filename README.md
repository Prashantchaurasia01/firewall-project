# firewall-project
Build and configure a firewall

Firewall Project – UFW & Nmap
 Overview

This project demonstrates how to configure firewall rules using UFW (Uncomplicated Firewall) on Linux and verify their effectiveness using Nmap.
The goal is to:

Allow only necessary traffic.

Deny insecure or unwanted connections.

Test the firewall rules with network scanning tools.

 Step 1 – Firewall Configuration (UFW)

Enabled UFW and applied rules:

# Allow SSH, HTTP, HTTPS
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Allow custom TCP range (1000–2000)
sudo ufw allow 1000:2000/tcp

# Allow from specific host
sudo ufw allow from 192.168.1.100

# Allow from LAN subnet
sudo ufw allow from 192.168.1.0/24

# Deny insecure Telnet
sudo ufw deny 23/tcp

# Block malicious IP
sudo ufw deny from 203.0.113.0

# Check status
sudo ufw status verbose

Screenshot 1: Nmap Scan Result.
Screenshot 2: Example UFW rules applied successfully.

 Step 2 – Firewall Testing (Nmap)

After applying rules, tested using Nmap with aggressive scanning:

nmap -v -A 172.29.223.0/24


Nmap reported all hosts as down.

This means the firewall successfully blocked or filtered incoming probes.

 Results:

Before UFW rules: all ports were visible to Nmap.

After applying UFW rules: device became stealthy, and Nmap scans returned no active hosts.

Only allowed services (22, 80, 443, 1000–2000) are accessible; all others are blocked.

Conclusion:

This project shows how a properly configured firewall:

Protects against unauthorized scans.

Hides the system from attackers.

Restricts access to only trusted IPs and services.

Using UFW with Nmap testing provides a practical way to secure Linux systems.

Tools Used:

UFW (Uncomplicated Firewall)

Nmap (Network Mapper)

Kali Linux
