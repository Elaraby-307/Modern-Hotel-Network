# 🏨 Modern Hotel Network — ITI Summer Internship

A complete **Cisco CCNA networking project** designed and implemented as part of the **ITI Summer Internship — CCNA Network Course**.

The project simulates a modern hotel's network infrastructure across three floors, with VLAN segmentation, inter-router routing, DHCP, OSPF, wireless connectivity, network services, SSH management, ACL security, NTP synchronization, and switch port security.

---

## 📌 Project Overview

The hotel consists of **three floors**, each connected through a dedicated router and switch.

### 🏢 Floor & Department Structure

| Floor | Department | VLAN | Network |
|---|---|---:|---|
| 1st Floor | Reception | 80 | `192.168.8.0/24` |
| 1st Floor | Store | 70 | `192.168.7.0/24` |
| 1st Floor | Logistics | 60 | `192.168.6.0/24` |
| 2nd Floor | Finance | 50 | `192.168.5.0/24` |
| 2nd Floor | HR | 40 | `192.168.4.0/24` |
| 2nd Floor | Sales / Marketing | 30 | `192.168.3.0/24` |
| 3rd Floor | Admin | 20 | `192.168.2.0/24` |
| 3rd Floor | IT | 10 | `192.168.1.0/24` |

---

## 🌐 Network Architecture

The network contains:

- 3 Cisco routers
- 3 switches — one per floor
- Department-specific VLANs
- Wi-Fi networks on every floor
- Laptops and mobile devices
- A printer for each department
- `Test-PC` in the IT department
- `hotel-server` providing NTP services
- Serial DCE links between routers

All routers are located in the **IT department server room**.

### 🔗 Inter-Router Networks

| Link | Network |
|---|---|
| Router 1 ↔ Router 2 | `10.10.10.0/30` |
| Router 1 ↔ Router 3 | `10.10.10.4/30` |
| Router 2 ↔ Router 3 | `10.10.10.8/30` |

The router-to-router connections use **Serial DCE cables** with the **HWIC-2T** module.

---

## 🛠️ Technologies & Concepts Implemented

### Routing
- OSPF
- Multi-area-ready OSPF design using Area 0
- Inter-router routing
- Router IDs

### Switching
- VLANs
- Trunking
- Router-on-a-Stick
- Port Security
- Sticky MAC address learning

### Network Services
- DHCP
- NTP
- SSH

### Security
- Extended ACLs
- ICMP filtering
- HTTPS-only access policy
- Port Security with shutdown violation mode

### Wireless
- Wi-Fi connectivity
- Laptop and smartphone clients

---

## 🔐 Security Requirements Implemented

### HR & Sales → Hotel Server

Ping traffic from:

- VLAN 40 — HR
- VLAN 30 — Sales / Marketing

to the `hotel-server` is blocked.

### Store → Hotel Server

The Store VLAN is allowed to access the `hotel-server` using **HTTPS only**.

### IT Switch Port Security

`Test-PC` is connected to:

```text
Fa0/20
```

Port security is configured to:

- Allow only `Test-PC`
- Learn the MAC address using **sticky MAC**
- Shut down the interface when a violation occurs

---

## 🖥️ Management & Services

### DHCP

Each floor's router acts as a DHCP server.

Devices automatically receive:

- IP address
- Subnet mask
- Default gateway

from their corresponding DHCP pool.

### SSH

SSH is configured on all routers for secure remote management.

The IT department contains:

```text
Test-PC
```

which is used to test remote SSH login to the routers.

### NTP

The server:

```text
hotel-server
```

is configured as the **NTP Server** for the routers and switches across the network.

---

## 🧪 Verification

The implementation can be verified using commands such as:

```bash
show ip interface brief
show vlan brief
show interfaces trunk
show ip route
show ip ospf neighbor
show ip ospf interface
show ip dhcp binding
show access-lists
show port-security
show port-security interface fa0/20
show clock
show ntp status
show ntp associations
```

SSH connectivity can be tested from `Test-PC`.

Connectivity between VLANs can be tested with:

```bash
ping <destination-ip>
```

while security policies can be verified by testing the restricted traffic described above.

---

## 📚 Skills Demonstrated

Through this project, the following CCNA concepts were applied practically:

- IPv4 Addressing
- Subnetting
- VLAN Configuration
- Trunking
- Router-on-a-Stick
- DHCP
- OSPF
- Serial DCE
- SSH
- ACLs
- NTP
- Port Security
- Wireless Networking
- Network Troubleshooting
- Cisco IOS Configuration
- Network Documentation

---

## 👨‍💻 Project Context

**Program:** ITI Summer Internship  
**Course:** CCNA Network Course  
**Project:** Modern Hotel Network Design & Implementation

This project represents a practical application of Cisco networking concepts in a multi-floor enterprise network environment.
