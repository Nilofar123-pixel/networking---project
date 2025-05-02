# networking---project
my personal project related to networking 
# Basic Cisco Packet Tracer Network Setup

This is a simple networking project created using Cisco Packet Tracer. It demonstrates a basic LAN setup with:

- 1 Router (2911)
- 2 Switches (2960)
- 2 PCs

The network is configured with static IP addresses, and connectivity is tested using ping.

## Objectives

- Understand basic router and switch configuration
- Learn IP address assignment
- Test end-to-end connectivity

## Tools Used

- Cisco Packet Tracer

## How to Run

1. Open the .pkt file in Cisco Packet Tracer.
2. Power on all devices.
3. Use the *Command Prompt* on each PC to test connectivity using the ping command.

## Status

The network is up and working — ping is successful between the PCs.
![Screenshot 2025-05-02 180151](https://github.com/user-attachments/assets/a68630b5-6c35-4155-b7ec-dbc9eb0b82b8)
![Screenshot 2025-05-02 180202](https://github.com/user-attachments/assets/632a12de-c48e-436b-bdde-d4fd85995378)




# Subnetting Lab – IP Design & Routing

## Overview

This project demonstrates subnetting and inter-network communication by designing a network for three departments: HR, IT, and Finance. Each department is assigned its own subnet using a /27 subnet mask, and connectivity is enabled using a router.

---

## Objectives

- Subnet a /24 network into three /27 subnets
- Assign each subnet to a department (HR, IT, Finance)
- Configure router interfaces and VLANs
- Enable successful ping communication between departments

---

## Devices Used

- 1 Router (Cisco 2911)
- 1 Switch (Cisco 2960)
- 3 PCs (1 per department)
- Copper straight-through cables

---

## IP Addressing Scheme

Base Network: 192.168.1.0/24  
Subnetting into /27 (each with 30 usable IPs):

| Department | Subnet Range        | Gateway        | PC IP           |
|------------|---------------------|----------------|-----------------|
| HR         | 192.168.1.0/27      | 192.168.1.1    | 192.168.1.10    |
| IT         | 192.168.1.32/27     | 192.168.1.33   | 192.168.1.40    |
| Finance    | 192.168.1.64/27     | 192.168.1.65   | 192.168.1.70    |

---

## Topology

![Screenshot 2025-05-03 042919](https://github.com/user-attachments/assets/53b8f460-e3ed-47e8-8291-a5f20d728c41)


[HR PC]     [IT PC]     [Finance PC] |           |             | +-----------+-------------+ | Switch | Router

---

## Configuration Steps

### 1. Set Up Devices

Place 1 Router, 1 Switch, and 3 PCs in Packet Tracer.

### 2. Connect Devices

- Connect all PCs to the switch using straight-through cables.
- Connect the switch to the router via G0/0 or F0/0.

### 3. Assign IPs to PCs

*HR PC:* 192.168.1.10 /27, Gateway 192.168.1.1  
*IT PC:* 192.168.1.40 /27, Gateway 192.168.1.33  
*Finance PC:* 192.168.1.70 /27, Gateway 192.168.1.65

### 4. Configure Router (Router-on-a-Stick or Sub-Interfaces)

```bash
enable
configure terminal

interface g0/0
no shutdown

interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.1.1 255.255.255.224
exit

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.1.33 255.255.255.224
exit

interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.1.65 255.255.255.224
exit

Testing Connectivity

Use each PC's Command Prompt to ping the others:

ping 192.168.1.40  # from HR to IT
ping 192.168.1.70  # from HR to Finance

Expected Output

Successful ping replies indicate that subnetting and routing are correctly configured.


---

Files in this Repository

subnetting-lab/
├── subnetting-lab.pkt      # Cisco Packet Tracer file
├── topology.png            # Network topology screenshot
├── README.md               # This documentation


---

Conclusion

This lab demonstrates practical skills in:

Subnetting

VLAN tagging

Router configuration

Inter-network communication

