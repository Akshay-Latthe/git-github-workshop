## Table of Contents

# Network Commands Reference Guide 🌐

1. [Network Configuration](#network-configuration)
2. [Network Diagnostics](#network-diagnostics)
3. [DNS Tools](#dns-tools)
4. [Network Security](#network-security)
5. [File Transfer](#file-transfer)
6. [Network Monitoring](#network-monitoring)

# Network Commands Reference Guide 🌐

## Network Configuration

### 1. `route` - Routing Table Management
**Description**: Manages network routing tables
```bash
# Show routing table in numeric format
route -n

```

### 2. `ip` - Modern Network Configuration
**Description**: Modern replacement for ifconfig/route
```bash
# Show all IP addresses
ip address show

# Add IP to interface
ip addr add 192.168.1.100/24 dev eth0

# Show routing table
ip route show
```

### 3. `ifconfig` - Interface Configuration (Legacy)
**Description**: Configure network interfaces
```bash
# Display all interfaces
ifconfig

# Set IP address
ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up
```

### 4. `iwconfig` - Wireless Configuration
**Description**: Configure wireless network interfaces
```bash
# Show wireless interface details
iwconfig wlan0

# Set wireless mode
iwconfig wlan0 mode managed
```

## Network Diagnostics

### 5. `ping` - Network Connectivity Test
**Description**: Test host reachability and latency
```bash
# Ping with count limit
ping -c 4 google.com

# Ping with specific interval
ping -i 2 google.com
```

### 6. `traceroute` - Path Tracing
**Description**: Show packet route to destination
```bash
# Trace with max hops
traceroute -m 15 google.com

# Numeric only output
traceroute -n google.com
```

### 7. `mtr` - Network Diagnostic Tool
**Description**: Combines ping and traceroute functionality
```bash
# Real-time network diagnostics
mtr google.com

# Report mode
mtr --report google.com
```

### 8. `ss` - Socket Statistics
**Description**: Modern replacement for netstat
```bash
# Show all TCP ports
ss -t

# Show listening ports with process
ss -tulnp
```

## DNS Tools

### 9. `nslookup` - Name Server Lookup
**Description**: Query DNS records
```bash
# Basic DNS lookup
nslookup google.com

# Query specific record type
nslookup -type=mx google.com
```

### 10. `dig` - DNS Lookup Utility
**Description**: Advanced DNS querying tool
```bash
# Detailed DNS query
dig google.com

# Query specific record
dig google.com MX
```

### 11. `whois` - Domain Information
**Description**: Query domain registration details
```bash
# Basic domain lookup
whois google.com

# Specific whois server
whois -h whois.verisign-grs.com google.com
```

## Network Security

### 12. `nmap` - Network Scanner
**Description**: Security scanner for network exploration
```bash
# Basic scan
nmap -v example.com

# Comprehensive scan
nmap -A -T4 example.com
```

### 13. `iptables` - Firewall Management
**Description**: Configure kernel firewall
```bash
# List all rules
sudo iptables -L

# Allow incoming SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

## File Transfer

### 14. `wget` - Web File Download
**Description**: Download files from web servers
```bash
# Download file
wget https://example.com/file.zip

# Resume partial download
wget -c https://example.com/large-file.iso
```

### 15. `curl` - Data Transfer Tool
**Description**: Transfer data from/to servers
```bash
# GET request
curl https://api.example.com

# POST request with data
curl -X POST -d "data=value" https://api.example.com
```

## Network Monitoring

### 16. `watch` - Command Monitor
**Description**: Execute command periodically
```bash
# Monitor network connections
watch -n 5 'netstat -tuln'

# Watch with differences highlighted
watch -d -n 2 'ps aux'
```

### 17. `netcat (nc)` - Network Swiss Army Knife
**Description**: Read/write network connections
```bash
# Listen on port
nc -l 8080

# Connect to port
nc example.com 80
```

### 18. `arp` - Address Resolution Protocol
**Description**: View/modify ARP cache
```bash
# Show ARP cache
arp -n

# Delete ARP entry
arp -d 192.168.1.100
```

## Common Workflow Examples

### Basic Network Troubleshooting
```bash
# Check connectivity
ping -c 4 google.com

# Trace route
traceroute google.com

# DNS lookup
dig google.com

# Port scan
nmap -p 80,443 google.com
```

### Security Audit
```bash
# Port scan
nmap -sV target.com

# Check firewall
iptables -L

# Monitor connections
watch -n 1 'netstat -tuln'
```

## Tips
- Always backup network configurations before changes
- Use `watch` to monitor changing network status
- Combine tools for comprehensive diagnostics
- Document network changes and configurations
#=========================================================================================================================
