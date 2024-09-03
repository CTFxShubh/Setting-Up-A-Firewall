# FUTURE_CS_02
## Setting Up a Firewall

## Introduction to UFW (Uncomplicated Firewall)

UFW is a user-friendly command-line tool designed to manage firewall rules on Linux distributions such as Ubuntu, Debian, and Arch Linux. It serves as a simplified interface for managing iptables, the underlying packet filtering framework.

## Installation of UFW

To install UFW, use the following command:

```bash
sudo apt-get install ufw
```

## Basic UFW Commands

1. Enabling and Disabling the Firewall

-> Enable UFW: Activates the firewall.

```bash
sudo ufw enable
```

-> Disable UFW: Deactivates the firewall.

```bash
sudo ufw disable
```

2. Checking the Status

-> Status: Displays the current status of the firewall and lists active rules.

```bash
sudo ufw status
```

-> Verbose Status: Provides detailed information about the firewall status.

```bash
sudo ufw status verbose
```

3. Allowing and Denying Traffic

-> Allow a Port: Permits traffic on a specific port.

```bash
sudo ufw allow [port]
```

Example: Allow HTTP traffic on port 80

```bash
sudo ufw allow 80
```

-> Deny a Port: Blocks traffic on a specific port.

```bash
sudo ufw deny [port]
```

Example: Deny HTTP traffic on port 80

```bash
sudo ufw deny 80
```

4. Allowing/Denying by IP Address

-> Allow by IP: Allows traffic from a specified IP address.

```bash
sudo ufw allow from [IP_address]
```

Example: Allow traffic from 192.168.1.1

```bash
sudo ufw allow from 192.168.1.1
```

-> Deny by IP: Blocks traffic from a specified IP address.

```bash
sudo ufw deny from [IP_address]
```

Example: Deny traffic from 192.168.1.1

```bash
sudo ufw deny from 192.168.1.1
```

5. Default Policies

Configure default policies for incoming and outgoing traffic.

```bash
sudo ufw default allow outgoing
sudo ufw default deny incoming
```

6. Deleting Rules

**Delete by Rule Number**: Removes a rule by specifying its number from the status list.

```bash
sudo ufw delete [rule_number]
```

**Delete by Specification:** Removes a rule by specifying the exact rule.

```bash
sudo ufw delete allow 80
```

## Advanced UFW Commands

1. Allowing Specific Services

UFW supports predefined service names listed in /etc/services.
bash
Copy code
sudo ufw allow ssh
sudo ufw allow http
Allowing/Denying Ranges of IP Addresses

Allow or deny a range of IP addresses.
bash
Copy code
sudo ufw allow from 192.168.0.0/24
sudo ufw deny from 192.168.0.0/24
Rate Limiting

Implement rate limiting to protect against brute-force attacks.
bash
Copy code
sudo ufw limit ssh/tcp
Logging
Enable Logging: Activates logging to monitor firewall activity.
bash
Copy code
sudo ufw logging on
Set Log Level: Adjusts the verbosity of the log.
bash
Copy code
sudo ufw logging low
sudo ufw logging medium
sudo ufw logging high
Practical Examples
Allowing HTTP and HTTPS Traffic

bash
Copy code
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
Allowing SSH Access Only from a Specific IP

bash
Copy code
sudo ufw allow from 192.168.1.100 to any port 22
Denying All Incoming Traffic Except for SSH

bash

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
Setting Up Rate Limiting for SSH

bash
Copy code
sudo ufw limit 22/tcp
Conclusion
UFW provides a straightforward interface for managing firewall rules on Linux systems, enhancing security by controlling network traffic. By utilizing the above commands and examples, users can effectively configure and manage their firewall settings to meet their security needs.
