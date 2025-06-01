# Task-4-Setup-and-Use-a-Firewall-on-Windows-or-Linux

The primary objective is to configure and test basic firewall rules to allow or block network traffic. This task aims to develop fundamental firewall management skills and an understanding of network traffic filtering.

Tools: UFW (Uncomplicated Firewall)

Mini-Guide: Firewall Configuration Steps & Commands (UFW on Linux)
1. Open Firewall Configuration Tool (Terminal):
* UFW is managed via the command line. Open your terminal.

2. List Current Firewall Rules:
* Check UFW status and rules:

sudo ufw status verbose

3. Add a Rule to Block Inbound Traffic on a Specific Port (e.g., Port 23 for Telnet):
* Disable Telnet (port 23):

sudo ufw deny 23/tcp

* Enable UFW if it's not already:

sudo ufw enable

(You will be prompted to confirm. Type y and press Enter.)

4. Test the Rule:
* Attempt to connect to port 23 locally or remotely.
* Local Test (from another terminal window or machine):

telnet localhost 23

(Expected result: Connection refused or timeout)
* Using nc (netcat):

nc -vz localhost 23

(Expected result: Connection refused)

5. Add Rule to Allow SSH (Port 22):
* Allow SSH connections:

sudo ufw allow ssh
# Or specifically for port 22:
sudo ufw allow 22/tcp

6. Remove the Test Block Rule:
* Delete the rule by its number (from sudo ufw status numbered):

sudo ufw status numbered
# Find the rule number for 'deny 23/tcp'
sudo ufw delete [rule_number]

* Alternatively, delete by the rule itself:

sudo ufw delete deny 23/tcp

Summary: A firewall acts as a security guard for a network, controlling incoming and outgoing network traffic based on a set of predefined security rules. It monitors traffic flow and decides whether to allow or block specific data packets.
