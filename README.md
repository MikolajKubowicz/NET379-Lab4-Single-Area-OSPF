# NET 379 Lab 4 - Single-Area OSPF

This project demonstrates the configuration and troubleshooting of a single-area OSPF network using Cisco Modeling Labs (CML).

## Lab Overview

The lab consists of four Cisco routers configured in OSPF Area 0. The goal was to configure OSPF, verify neighbor relationships, analyze OSPF adjacency formation, and observe how changes to OSPF cost affect routing decisions.

## Technologies Used

- Cisco Modeling Labs (CML)
- Cisco IOS
- OSPF
- IPv4
- Dynamic Routing
- Dijkstra Shortest Path First Algorithm

## Network Configuration

The topology includes four routers:

- R1
- R2
- R3
- R4

All routers participate in OSPF Area 0.

### Main Networks

- 10.1.1.0/24
- 10.10.10.0/30
- 10.20.20.0/30
- 172.16.40.0/24
- 172.16.41.0/24
- 192.168.30.0/24
- 10.3.3.0/24

## What I Implemented

- Configured IPv4 addressing on router interfaces
- Configured simulated WAN bandwidth values
- Implemented OSPF process 1 on all routers
- Advertised all required networks into OSPF Area 0
- Verified OSPF neighbor adjacencies
- Analyzed DR, BDR, and DROTHER roles
- Captured OSPF adjacency debug messages
- Changed the R3-R4 OSPF network type to point-to-point
- Observed adjacency rebuilding after the network type change
- Modified OSPF interface costs to influence routing decisions
- Verified route changes using `show ip route`
- Applied Dijkstra's Shortest Path First logic to determine the preferred path

## OSPF Adjacency Analysis

During the lab, I captured the OSPF adjacency process between routers. The routers progressed through states including:

- 2-Way
- EXSTART
- EXCHANGE
- LOADING
- FULL

This demonstrated how OSPF routers discover neighbors, exchange database information, and synchronize their link-state databases.

## OSPF Cost Manipulation

The R2-R3 link was assigned an OSPF cost of 10000, causing OSPF to prefer the alternate path through R4.

The R3-R4 link was later assigned a cost of 20000, causing OSPF to prefer the R2-R3 path again.

This demonstrated how OSPF chooses routes based on the lowest total path cost.

## Verification Commands

Some of the Cisco IOS commands used during the lab include:

```bash
show ip interface brief
show ip ospf
show ip ospf neighbor
show ip ospf interface brief
show ip protocols
show ip route
debug ip ospf adj
