# Net Practice - 42 School Project

## Overview
Net Practice is a networking exercise project from 42 school that focuses on understanding TCP/IP addressing, subnetting, and routing. This project helps you learn how to configure small-scale networks through practical exercises.

## What You'll Learn
- **IP Addressing**: Understanding IPv4 addresses and their structure
- **Subnetting**: Calculating subnet masks and network ranges
- **Routing**: Configuring routes between networks
- **Network Troubleshooting**: Identifying and fixing network configuration issues

## Project Structure
```
net_practice/
├── README.md           # This file
├── index.html          # Interactive practice interface
├── levels/             # Practice exercises (Level 1-10)
│   ├── level1.json
│   ├── level2.json
│   ├── ...
│   └── level10.json
├── solutions/          # Detailed solutions and explanations
│   └── solutions.md
└── resources/          # Learning materials
    └── networking_basics.md
```

## How to Use

### Option 1: Interactive Interface (Recommended)
1. Open `index.html` in your web browser
2. Select a level to practice
3. Fill in the required IP addresses, subnet masks, and routes
4. Check your solution to see if it's correct

### Option 2: Manual Practice
1. Navigate to the `levels/` directory
2. Open a level JSON file
3. Configure the network parameters
4. Verify your solution against the requirements

## Getting Started

### Prerequisites
- Basic understanding of binary numbers
- Familiarity with IP address notation (e.g., 192.168.1.1)
- A web browser (for interactive mode)

### Quick Start
1. Clone this repository
2. Open `index.html` in your browser
3. Start with Level 1 and progress through the levels
4. Refer to `resources/networking_basics.md` if you need help with concepts

## Levels Overview

### Level 1-3: Basic IP Addressing
Introduction to IP addresses and simple network configurations

### Level 4-6: Subnetting
Learn to work with subnet masks and network divisions

### Level 7-9: Routing
Configure routes between different networks

### Level 10: Advanced
Combine all concepts in a complex network scenario

## Resources
- See `resources/networking_basics.md` for fundamental networking concepts
- See `solutions/solutions.md` for detailed explanations of each level

## Learning Tips
1. **Understand Binary**: IP addresses are binary numbers. Practice binary-to-decimal conversion
2. **Master Subnet Masks**: Learn how subnet masks define network boundaries
3. **Practice Routing**: Understand how routers forward packets between networks
4. **Use Visual Tools**: Draw network diagrams to visualize connections
5. **Check Your Work**: Use online subnet calculators to verify your calculations

## Common IP Address Ranges

### Private IP Ranges (RFC 1918)
- **Class A**: 10.0.0.0 to 10.255.255.255 (10.0.0.0/8)
- **Class B**: 172.16.0.0 to 172.31.255.255 (172.16.0.0/12)
- **Class C**: 192.168.0.0 to 192.168.255.255 (192.168.0.0/16)

### Special Addresses
- **Loopback**: 127.0.0.0/8 (typically 127.0.0.1)
- **Link-Local**: 169.254.0.0/16
- **Default Route**: 0.0.0.0/0

## Subnet Mask Reference
| CIDR | Subnet Mask     | Usable Hosts |
|------|----------------|--------------|
| /24  | 255.255.255.0  | 254          |
| /25  | 255.255.255.128| 126          |
| /26  | 255.255.255.192| 62           |
| /27  | 255.255.255.224| 30           |
| /28  | 255.255.255.240| 14           |
| /29  | 255.255.255.248| 6            |
| /30  | 255.255.255.252| 2            |

## Contributing
This is a personal practice project. Feel free to fork and adapt for your own learning!

## Credits
Based on the Net Practice project from 42 School

## License
This project is created for educational purposes.