# networking---project
my personal project related to networking
# Basic Cisco Packet Tracer Network Setup
## overview
This project demonstrates a basic network setup using Cisco Packet Tracer. It includes a router, two switches, and two PCs configured with IP addressing and connectivity tested using ping.

## Objectives

- Understand basic router and switch configuration
- Learn IP address assignment
- Test end-to-end connectivity
  
----  
## deivice used
- 1 Router - Cisco 2911
- 2 Switches Cisco 2960
- 2 PCs Generic PCs
- Copper Straight-through Cables - For connecting router to switches and PCs to switches

## IP Address Scheme

| Device  | Interface          | IP Address     | Subnet Mask    |
|---------|--------------------|----------------|----------------|
| PC0     | FastEthernet0      | 192.168.1.10   | 255.255.255.0  |
| Router  | GigabitEthernet0/0 | 192.168.1.1    | 255.255.255.0  |
| Router  | GigabitEthernet0/1 | 192.168.2.1    | 255.255.255.0  |
| PC1     | FastEthernet0      | 192.168.2.10   | 255.255.255.0  |

## Default Gateways

- PCO: 192.168.1.1
- PC1: 192.168.2.1

## topology
![Screenshot 2025-05-02 180202](https://github.com/user-attachments/assets/5b12fb8c-90ae-4e93-a068-66bed2f25069)


## configuration steps
### 1. Set Up Devices
Place 1 Router, 2 Switch, and 2 PCs in Packet Tracer.

## configure router
bash
enable
configure terminal
hostname Router
interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface g0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

## Test connectivity
ping 192.168.0.2   # from PC0 to PC1  
ping 192.168.0.1   # from PC1 to PC0


## Tools Used
- Cisco Packet Tracer

## How to Run

1. Open the .pkt file in Cisco Packet Tracer.
2. Power on all devices.
3. Use the *Command Prompt* on each PC to test connectivity using the ping command.

## Status
The network is up and working — ping is successful between the PCs.
![Screenshot 2025-05-02 180151](https://github.com/user-attachments/assets/67b340f3-fb6d-4dde-90c4-e5e29e1ff901)





## Subnetting Lab – IP Design & Routing

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


---

## Configuration Steps

### 1. Set Up Devices

Place 1 Router, 1 Switch, and 3 PCs in Packet Tracer.

### 2. Connect Devices

- Connect all PCs to the switch using straight-through cables.
- Connect the switch to the router via G0/0 or F0/0.


### 4. Configure Router (Router-on-a-Stick or Sub-Interfaces)

bash
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

## Testing Connectivity

Use each PC's Command Prompt to ping the others:

ping 192.168.1.40  # from HR to IT
ping 192.168.1.70  # from HR to Finance

## Expected Output

Successful ping replies indicate that subnetting and routing are correctly configured.


## Status

-The subnetted network is successfully configured.
-All departments (HR, IT, Finance) are assigned to different subnets.
-Router-on-a-stick configuration enables inter-VLAN routing.
-All PCs can successfully ping each other across subnets, proving full connectivity.

![Screenshot 2025-05-03 041802](https://github.com/user-attachments/assets/819bcdfe-0c4a-4f9a-b196-c40961a1790b)
