# FUTURE_CS_02
Setting Up a Firewall

### Detailed Explanation of UFW Configuration:

#### **Introduction to UFW (Uncomplicated Firewall)**
UFW is a command-line tool used to manage firewall rules on Linux distributions like Ubuntu, Debian, and Arch Linux. It is designed to simplify the management of iptables, the underlying packet filtering framework.

#### **Installing UFW**
If UFW is not already installed, you can install it using the following command:
```bash
sudo apt-get install ufw
```

#### **Basic UFW Commands**

1. **Enabling and Disabling the Firewall**
   - **Enable UFW**: This command turns on the firewall.
     ```bash
     sudo ufw enable
     ```
   - **Disable UFW**: This command turns off the firewall.
     ```bash
     sudo ufw disable
     ```

2. **Checking the Status**
   - **Status**: Check if the firewall is active and list current rules.
     ```bash
     sudo ufw status
     ```
   - **Verbose Status**: More detailed information about the firewall status.
     ```bash
     sudo ufw status verbose
     ```

3. **Allowing and Denying Traffic**
   - **Allow a Port**: Allow traffic on a specific port.
     ```bash
     sudo ufw allow [port]
     ```
     Example: Allow HTTP traffic
     ```bash
     sudo ufw allow 80
     ```
   - **Deny a Port**: Block traffic on a specific port.
     ```bash
     sudo ufw deny [port]
     ```
     Example: Deny HTTP traffic
     ```bash
     sudo ufw deny 80
     ```

4. **Allow/Deny by IP Address**
   - **Allow by IP**: Allow traffic from a specific IP.
     ```bash
     sudo ufw allow from [IP_address]
     ```
     Example: Allow traffic from 192.168.1.1
     ```bash
     sudo ufw allow from 192.168.1.1
     ```
   - **Deny by IP**: Block traffic from a specific IP.
     ```bash
     sudo ufw deny from [IP_address]
     ```
     Example: Deny traffic from 192.168.1.1
     ```bash
     sudo ufw deny from 192.168.1.1
     ```

5. **Default Policies**
   - Set default incoming and outgoing policies.
     ```bash
     sudo ufw default allow outgoing
     sudo ufw default deny incoming
     ```

6. **Deleting Rules**
   - **Delete by Rule Number**: Remove a rule using its number from the status list.
     ```bash
     sudo ufw delete [rule_number]
     ```
   - **Delete by Specification**: Remove a rule by specifying the exact rule.
     ```bash
     sudo ufw delete allow 80
     ```

#### **Advanced UFW Commands**

1. **Allowing Specific Services**
   - UFW recognizes certain service names defined in `/etc/services`.
     ```bash
     sudo ufw allow ssh
     sudo ufw allow http
     ```

2. **Allowing/Denying Ranges of IP Addresses**
   - Allow or deny a range of IP addresses.
     ```bash
     sudo ufw allow from 192.168.0.0/24
     sudo ufw deny from 192.168.0.0/24
     ```

3. **Rate Limiting**
   - Protect against brute-force attacks by rate limiting.
     ```bash
     sudo ufw limit ssh/tcp
     ```

#### **Logging**
   - **Enable Logging**: Turn on logging to monitor firewall activity.
     ```bash
     sudo ufw logging on
     ```
   - **Set Log Level**: Define the verbosity of the log.
     ```bash
     sudo ufw logging low
     sudo ufw logging medium
     sudo ufw logging high
     ```

#### **Practical Examples**

1. **Allowing HTTP and HTTPS Traffic**
   ```bash
   sudo ufw allow 80/tcp
   sudo ufw allow 443/tcp
   ```

2. **Allowing SSH Only from a Specific IP**
   ```bash
   sudo ufw allow from 192.168.1.100 to any port 22
   ```

3. **Denying All Incoming Traffic Except for SSH**
   ```bash
   sudo ufw default deny incoming
   sudo ufw default allow outgoing
   sudo ufw allow 22/tcp
   ```

4. **Setting up Rate Limiting for SSH**
   ```bash
   sudo ufw limit 22/tcp
   ```

#### **Conclusion**
UFW simplifies firewall management with easy-to-use commands. Properly configuring UFW enhances the security of your Linux system by controlling the traffic that is allowed to and from the system.



