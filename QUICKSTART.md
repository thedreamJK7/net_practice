# Quick Start Guide

Welcome to Net Practice! This guide will help you get started quickly.

## What is Net Practice?

Net Practice is a hands-on learning project from 42 School that teaches you TCP/IP networking through practical exercises. You'll configure IP addresses, subnet masks, and routes to make networks work correctly.

## Getting Started in 3 Steps

### Step 1: Open the Interface
Simply open `index.html` in your web browser (Chrome, Firefox, Safari, or Edge).

No installation required! Everything runs in your browser.

### Step 2: Start with Level 1
1. Click on "Level 1" button
2. Read the description and requirements
3. Fill in the empty fields with appropriate values
4. Click "Check Solution" to verify

### Step 3: Learn and Progress
- If stuck, read the hints
- Refer to the Networking Basics Guide for concepts
- Check the Solutions guide when needed
- Progress through all 10 levels

## Tips for Success

1. **Start Simple**: Begin with Level 1 and work your way up
2. **Understand, Don't Memorize**: Focus on learning the concepts
3. **Use the Guides**: The networking basics guide has everything you need
4. **Practice Binary**: Understanding binary helps with subnetting
5. **Draw It Out**: Sketch the network topology on paper

## Key Concepts You'll Learn

### IP Addresses
- Format: `192.168.1.10`
- Four numbers (octets) from 0-255
- Uniquely identifies devices on a network

### Subnet Masks
- Format: `255.255.255.0` or `/24`
- Determines which part is network and which is host
- Larger number = smaller network

### Default Gateway
- The router's IP address on your network
- Where packets go to reach other networks
- Must be on the same subnet as your device

### Routing
- How packets travel between different networks
- Routers forward packets based on routing tables
- Default route (0.0.0.0/0) for Internet access

## Common Patterns

### /24 Network
- Mask: `255.255.255.0`
- 254 usable IPs (.1 to .254)
- First 3 octets must match
- Example: `192.168.1.0/24`

### /30 Network (Point-to-Point)
- Mask: `255.255.255.252`
- Only 2 usable IPs
- Perfect for router-to-router connections
- Networks start at multiples of 4

### Default Gateway
- Usually .1 or .254 in the subnet
- Must be on the same network as the host
- Example: Host at `192.168.1.10/24` → Gateway at `192.168.1.1`

## Troubleshooting

### "Hosts can't communicate"
✓ Check if they're on the same subnet
✓ Verify subnet masks match
✓ Ensure IPs are in the same network range

### "Can't reach other networks"
✓ Configure default gateway
✓ Verify gateway is on same subnet
✓ Check router has route to destination

### "Overlapping networks"
✓ Use the magic number method (256 - last octet of mask)
✓ Ensure networks don't share address space
✓ Plan your subnetting before assigning IPs

## Resources

### In This Project
- **README.md**: Full project documentation
- **resources/networking_basics.md**: Complete networking guide
- **solutions/solutions.md**: Detailed solutions for all levels

### Online Tools
- Subnet calculators (search "subnet calculator")
- Binary to decimal converters
- IP address calculators

## Practice Workflow

1. **Read the level description** - Understand what's required
2. **Analyze the topology** - See what devices are connected
3. **Plan your addresses** - Decide on IP ranges
4. **Fill in the fields** - Enter your configuration
5. **Check your work** - Use the Check Solution button
6. **Review and learn** - Understand why the solution works

## Need Help?

1. Read the **hints** for each level
2. Check the **networking_basics.md** guide
3. Look at the **solutions.md** for detailed explanations
4. Draw the network diagram on paper
5. Work through the examples in the guides

## Your First Exercise

Let's try Level 1 together:

**Given:**
- Client A: IP `104.95.23.12`, Mask: _(empty)_
- Client B: IP _(empty)_, Mask: `255.255.255.0`

**Solution:**
- Client A needs mask: `255.255.255.0` (or `/24`)
- Client B needs IP: `104.95.23.X` where X is 1-254 (except 12)
- Example: `104.95.23.13`

**Why?**
- Both must be on same network to communicate
- `/24` mask means first 3 octets match: `104.95.23`
- Last octet can be any valid host: 1-254

## Ready to Start?

Open `index.html` and begin your networking journey!

Good luck! 🚀
