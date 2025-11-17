# Networking Basics for Net Practice

## Introduction
This guide covers fundamental networking concepts needed to complete the Net Practice exercises.

## IP Addresses

### What is an IP Address?
An IP address (Internet Protocol address) is a unique numerical identifier assigned to each device on a network. In IPv4 (which we focus on), an IP address consists of 4 numbers (octets) separated by dots.

**Example**: `192.168.1.10`

### IP Address Structure
- Each octet is a number from 0 to 255
- IP addresses are actually 32-bit binary numbers
- Example: `192.168.1.10` in binary is `11000000.10101000.00000001.00001010`

### IP Address Classes (Historical)
| Class | First Octet Range | Default Mask | Purpose |
|-------|------------------|--------------|---------|
| A     | 1-126           | 255.0.0.0    | Large networks |
| B     | 128-191         | 255.255.0.0  | Medium networks |
| C     | 192-223         | 255.255.255.0| Small networks |

**Note**: Modern networks use CIDR (Classless Inter-Domain Routing) instead of classes.

## Subnet Masks

### Purpose
A subnet mask determines which part of an IP address represents the network and which part represents the host.

### How Subnet Masks Work
- Written like an IP address: `255.255.255.0`
- In binary, it's a series of 1s followed by 0s
- 1s represent the network portion
- 0s represent the host portion

**Example**:
```
IP Address:    192.168.1.10    = 11000000.10101000.00000001.00001010
Subnet Mask:   255.255.255.0   = 11111111.11111111.11111111.00000000
Network Part:  192.168.1       (first 24 bits)
Host Part:     10              (last 8 bits)
```

### CIDR Notation
CIDR notation uses a slash followed by the number of network bits.

**Examples**:
- `/24` = `255.255.255.0` (24 network bits, 8 host bits)
- `/25` = `255.255.255.128` (25 network bits, 7 host bits)
- `/30` = `255.255.255.252` (30 network bits, 2 host bits)

### Common Subnet Masks

| CIDR | Subnet Mask       | Binary (last octet) | Addresses | Usable Hosts |
|------|-------------------|---------------------|-----------|--------------|
| /24  | 255.255.255.0     | 00000000           | 256       | 254          |
| /25  | 255.255.255.128   | 10000000           | 128       | 126          |
| /26  | 255.255.255.192   | 11000000           | 64        | 62           |
| /27  | 255.255.255.224   | 11100000           | 32        | 30           |
| /28  | 255.255.255.240   | 11110000           | 16        | 14           |
| /29  | 255.255.255.248   | 11111000           | 8         | 6            |
| /30  | 255.255.255.252   | 11111100           | 4         | 2            |

## Subnetting

### Why Subnet?
- Organize networks into smaller segments
- Improve network performance
- Enhance security
- Efficient use of IP addresses

### Calculating Subnets

#### Example 1: Simple /24 Network
Network: `192.168.1.0/24`
- Network Address: `192.168.1.0` (first address)
- Broadcast Address: `192.168.1.255` (last address)
- Usable IPs: `192.168.1.1` to `192.168.1.254` (254 hosts)

#### Example 2: Dividing a /24 into Two /25 Networks
Original: `192.168.1.0/24`

Subnet 1: `192.168.1.0/25`
- Range: `192.168.1.0` to `192.168.1.127`
- Usable: `192.168.1.1` to `192.168.1.126`

Subnet 2: `192.168.1.128/25`
- Range: `192.168.1.128` to `192.168.1.255`
- Usable: `192.168.1.129` to `192.168.1.254`

### The Magic Number Method

For quick subnetting, use the "magic number":
1. Subtract the subnet mask octet from 256
2. This gives you the subnet size

**Example**: For `/26` (255.255.255.192)
- Magic Number: 256 - 192 = 64
- Subnets start at: 0, 64, 128, 192

So `192.168.1.0/26` networks are:
- `192.168.1.0/26` (0-63)
- `192.168.1.64/26` (64-127)
- `192.168.1.128/26` (128-191)
- `192.168.1.192/26` (192-255)

## Routing

### What is Routing?
Routing is the process of forwarding packets between different networks.

### Default Gateway
- The router's IP address on your local network
- Where packets go when they're destined for another network
- Must be on the same subnet as your host

**Example**:
```
Host IP: 192.168.1.10/24
Gateway: 192.168.1.1
```

### Routing Tables
Routers use routing tables to determine where to send packets.

**Format**:
```
Destination Network | Gateway | Interface
```

**Example**:
```
10.0.1.0/24        | 192.168.1.2 | eth0
10.0.2.0/24        | 192.168.1.3 | eth0
0.0.0.0/0          | 192.168.1.1 | eth0  (default route)
```

### Default Route
- Destination: `0.0.0.0/0` or `default`
- Used when no specific route matches
- Typically points to the Internet gateway

## Special IP Addresses

### Private IP Ranges (RFC 1918)
These can be used internally and are not routed on the Internet:
- **10.0.0.0/8**: 10.0.0.0 - 10.255.255.255
- **172.16.0.0/12**: 172.16.0.0 - 172.31.255.255
- **192.168.0.0/16**: 192.168.0.0 - 192.168.255.255

### Reserved Addresses
- **0.0.0.0**: Default route or "this network"
- **127.0.0.0/8**: Loopback (127.0.0.1 is localhost)
- **169.254.0.0/16**: Link-local (APIPA)
- **224.0.0.0/4**: Multicast
- **255.255.255.255**: Broadcast

### Network and Broadcast Addresses
- **Network Address**: First address in a subnet (all host bits = 0)
- **Broadcast Address**: Last address in a subnet (all host bits = 1)
- Both are reserved and cannot be assigned to hosts

## Binary Math for Networking

### Converting Decimal to Binary
Example: Convert 192 to binary
```
192 ÷ 2 = 96 remainder 0
96 ÷ 2 = 48 remainder 0
48 ÷ 2 = 24 remainder 0
24 ÷ 2 = 12 remainder 0
12 ÷ 2 = 6 remainder 0
6 ÷ 2 = 3 remainder 0
3 ÷ 2 = 1 remainder 1
1 ÷ 2 = 0 remainder 1

Read from bottom to top: 11000000
```

### Quick Powers of 2
| Power | Value | Common Use |
|-------|-------|------------|
| 2^0   | 1     |            |
| 2^1   | 2     |            |
| 2^2   | 4     | /30 networks |
| 2^3   | 8     | /29 networks |
| 2^4   | 16    | /28 networks |
| 2^5   | 32    | /27 networks |
| 2^6   | 64    | /26 networks |
| 2^7   | 128   | /25 networks |
| 2^8   | 256   | /24 networks |

## Practical Tips

### Checking if IPs are on Same Network
1. Convert IP and subnet mask to binary
2. Perform AND operation
3. Compare results

Or use this shortcut:
- For /24: First 3 octets must match
- For /16: First 2 octets must match
- For /8: First octet must match

### Common Mistakes to Avoid
1. **Using network or broadcast addresses as host IPs**
   - ❌ Bad: Using .0 or .255 in a /24 network
   - ✅ Good: Using .1 to .254 in a /24 network

2. **Overlapping subnets**
   - ❌ Bad: 192.168.1.0/25 and 192.168.1.64/26 overlap
   - ✅ Good: 192.168.1.0/25 and 192.168.1.128/25 don't overlap

3. **Incorrect default gateway**
   - ❌ Bad: Gateway on a different subnet than the host
   - ✅ Good: Gateway on the same subnet as the host

4. **Missing routes**
   - Routers need routes to all networks they must reach
   - Use default routes for Internet connectivity

## Practice Exercises

### Exercise 1: Identify Network Address
Given IP: `172.16.50.100/24`
- What is the network address? **Answer**: `172.16.50.0`
- What is the broadcast address? **Answer**: `172.16.50.255`
- What is the first usable IP? **Answer**: `172.16.50.1`
- What is the last usable IP? **Answer**: `172.16.50.254`

### Exercise 2: Same Network?
Are these IPs on the same network?
- IP1: `10.1.1.50/25`
- IP2: `10.1.1.200/25`

**Answer**: No
- IP1 network: `10.1.1.0/25` (0-127)
- IP2 network: `10.1.1.128/25` (128-255)

### Exercise 3: Subnetting
Divide `192.168.0.0/24` into 4 equal subnets.

**Answer**: Use /26 (4 subnets of 64 addresses each)
- `192.168.0.0/26` (0-63)
- `192.168.0.64/26` (64-127)
- `192.168.0.128/26` (128-191)
- `192.168.0.192/26` (192-255)

## Useful Commands

### Linux/Mac
```bash
# Show IP configuration
ip addr show
ifconfig

# Show routing table
ip route show
route -n

# Test connectivity
ping 192.168.1.1

# Trace route to destination
traceroute google.com
```

### Windows
```cmd
# Show IP configuration
ipconfig

# Show routing table
route print

# Test connectivity
ping 192.168.1.1

# Trace route to destination
tracert google.com
```

## Additional Resources

### Online Tools
- **Subnet Calculator**: Various online subnet calculators
- **IP Calculator**: For subnet and CIDR calculations
- **Visual Subnet Calculator**: For visual learners

### Further Reading
- RFC 791: Internet Protocol
- RFC 1918: Private IP Address Allocation
- RFC 4632: Classless Inter-domain Routing (CIDR)

## Summary

Key concepts to master:
1. **IP Addresses**: 32-bit numbers written as 4 octets
2. **Subnet Masks**: Define network vs. host portions
3. **CIDR Notation**: Shorthand for subnet masks (/24, /30, etc.)
4. **Subnetting**: Dividing networks into smaller segments
5. **Routing**: Forwarding packets between networks
6. **Default Gateway**: Router IP on your local network

Practice these concepts through the Net Practice levels, and refer back to this guide as needed!
