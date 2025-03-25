**Suricata-CUSTOM RULES  Firewall and Intrusion Detection System CONFIG
**
________________________________________________________________________

**Overview**

This project implements a firewall and intrusion detection system (IDS) using Suricata. It includes a set of custom rules designed to detect and mitigate various network threats. The project provides a configured suricata.yaml file to replace the default configuration, ensuring optimized performance and security monitoring.

**Features**

Custom Suricata rules for threat detection and prevention

Configurable network security policies

Real-time network traffic analysis

Supports rule customization for enhanced security

**Installation**

Step 1: Install Suricata

Ensure that Suricata is installed on your system. Use the following commands to install it:

**Ubuntu/Debian:**
```sh
sudo apt update
sudo apt install suricata -y
```


**CentOS/RHEL:**
```sh
sudo yum install epel-release -y
sudo yum install suricata -y
```
**From Source:**
```sh
git clone https://github.com/OISF/suricata.git
cd suricata
./configure && make && sudo make install-full
```
**Configuration**

Step 2: Replace Default Configuration

Navigate to the Suricata configuration directory:
```sh
cd /etc/suricata/
```
Replace the default suricata.yaml file with the one provided in this repository:
```sh
sudo cp /path/to/your/suricata.yaml /etc/suricata/suricata.yaml
```
Edit suricata.yaml to specify the correct network interface and home network IP address:
```sh
vars:
  address-groups:
    HOME_NET: "[Your_Home_IP]"
af-packet:
  - interface: eth0  # Replace with your actual network interface
```
Step 3: Copy Custom Rules

Copy the custom rules from the repository to the Suricata rules directory:
```sh
sudo cp /path/to/your/rules/* /etc/suricata/rules/
```
Ensure Suricata is configured to load the new rules by verifying the suricata.yaml file includes:

rule-files:
  - /etc/suricata/rules/*.rules

**Running Suricata**

To start Suricata with the configured settings:
```sh
sudo suricata -c /etc/suricata/suricata.yaml -i eth0
```
Replace eth0 with your actual network interface.

To run Suricata in daemon mode:
```sh
sudo systemctl start suricata
```
To check Suricata logs:
```sh
tail -f /var/log/suricata/suricata.log
```
**Updating Rules**

To manually update the rules and reload Suricata:
```sh
sudo suricata-update
sudo systemctl restart suricata
```
Verification

To test Suricata functionality, use a test rule:
```sh
echo "alert icmp any any -> any any (msg: 'ICMP test'; sid:1000001; rev:1;)" | sudo tee -a /etc/suricata/rules/test.rules
sudo systemctl restart suricata
ping -c 1 8.8.8.8
```
Check the logs for alerts:
```sh
grep 'ICMP test' /var/log/suricata/fast.log
```
License

This project is open-source and released under the MIT License.

Contact

For any inquiries or contributions, feel free to open an issue or submit a pull request on GitHub.

