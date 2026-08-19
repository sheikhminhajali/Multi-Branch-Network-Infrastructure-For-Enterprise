# 🌐 Multi-Branch Network Infrastructure For Enterprise

A Cisco Packet Tracer–based enterprise network simulation designed to demonstrate how multiple organizational branches can be interconnected, segmented, secured, and managed through a centralized network architecture.

This project models **six interconnected business locations** with wired and wireless users, VLANs, routing protocols, servers, VoIP devices, wireless infrastructure, and cloud connectivity.

---

## 📌 Project Overview

The network represents a realistic multi-branch enterprise environment consisting of:

* 🏢 Administration
* 🏭 Factory
* 🏬 Store
* 📦 Warehouse
* 💻 IT Department
* 🚚 Distribution Center

Each branch has its own LAN, addressing scheme, network devices, and end devices while maintaining communication with the other branches through the enterprise routing infrastructure.

The topology was developed and tested using **Cisco Packet Tracer**.

---

## 🗺️ Network Architecture

The enterprise network uses a hierarchical and distributed design in which branch routers provide connectivity between local networks and the wider enterprise.

### Branch Networks

| Branch              | Network                            | Main Purpose                         |
| ------------------- | ---------------------------------- | ------------------------------------ |
| Administration      | `192.168.6.0/24` and VLAN networks | Administrative users and departments |
| Store               | `192.168.1.0/24`                   | Retail users and POS devices         |
| Warehouse           | `192.168.2.0/24`                   | Warehouse operations and inventory   |
| IT Department       | `192.168.3.0/24`                   | IT users and network services        |
| Factory             | `192.168.4.0/24`                   | Production and factory users         |
| Distribution Center | `192.168.10.0/24`                  | Distribution and logistics           |

The WAN uses multiple point-to-point connections between routers to provide inter-branch communication and routing redundancy.

---

## 🖥️ Network & End Devices

### End Devices

The simulated environment contains:

* **15 PCs**
* **15 Laptops**
* **5 Smartphones**
* **3 Tablets**
* **2 IP Phones**
* **5 Printers**
* **4 Servers**

### Network Devices

The infrastructure includes:

* **6 Routers**

  * 3 × Cisco 1841
  * 3 × Cisco 2811
* **6 Switches**

  * 2 × Cisco 3560-24PS multilayer switches
  * 4 × Cisco 2960-24TT switches
* **2 Wireless LAN Controllers**

  * WLC-3504
* **2 Lightweight Access Points**

  * Aironet 3702i
* **3 Access Points**

  * Access Point-PT
* **1 DSL Modem**
* **1 Cloud-PT device**

---

## 🔀 Routing Architecture

The project demonstrates a **hybrid dynamic-routing environment** using RIPv2 and OSPF.

### RIPv2

RIPv2 is used across the initial router segment to demonstrate traditional dynamic routing and route exchange between selected branches.

### OSPF

OSPF is used across the remaining enterprise routers to provide scalable dynamic routing and faster convergence.

The topology demonstrates the concept of **route redistribution between routing domains**, allowing networks learned through different routing protocols to communicate.

### WAN Connectivity

The routers are interconnected using dedicated WAN links with separate addressing ranges such as:

```text
10.0.0.0/8
11.0.0.0/8
12.0.0.0/8
13.0.0.0/8
14.0.0.0/8
15.0.0.0/8
```

---

## 🧩 VLAN Segmentation

VLANs are used to logically separate different categories of users and services.

Example VLAN structure:

| VLAN | Purpose              |
| ---: | -------------------- |
|   10 | Administration       |
|   20 | HR                   |
|   30 | Finance              |
|   40 | Factory Staff        |
|   50 | Factory Devices      |
|   60 | Factory Wireless     |
|   70 | Store Users          |
|   80 | Store Devices        |
|   90 | Warehouse Users      |
|  100 | Warehouse Devices    |
|  110 | IT Users             |
|  120 | IT / Server Services |
|  130 | IT Printers          |
|  140 | Distribution Users   |
|  150 | Distribution Devices |

VLAN segmentation improves traffic organization and provides logical separation between different departments and device groups.

---

## 📡 Wireless Network

Wireless connectivity is implemented using both standalone access points and lightweight access points managed through Wireless LAN Controllers.

Configured wireless networks include:

| Location            | SSID        | Security |
| ------------------- | ----------- | -------- |
| Store               | `GUEST`     | WPA2-PSK |
| Store               | `Employee`  | WPA2-PSK |
| Warehouse           | `ware`      | WPA2-PSK |
| IT Department       | `ITd`       | WPA2-PSK |
| Factory             | `fac`       | WPA2-PSK |
| Distribution Center | `employees` | WPA2-PSK |

The WLC infrastructure provides centralized management for lightweight access points and simplifies wireless configuration across the enterprise.

> **Security note:** The passwords shown in the original project documentation are intended for a lab/simulation environment. Replace them with strong credentials before using similar configurations in a real network.

---

## 📡 DHCP

DHCP is used to automatically provide IP configuration to selected network clients.

The DHCP service simplifies the deployment of:

* Wireless clients
* Smartphones
* Tablets
* End-user computers
* Other dynamically addressed devices

Each DHCP scope is associated with the appropriate subnet and default gateway.

---

## 🌐 Inter-VLAN Routing

Router subinterfaces and multilayer switching are used to enable communication between VLANs.

For example:

```text
VLAN 10 → Administration
VLAN 20 → HR
VLAN 30 → Finance
```

Each VLAN receives a dedicated gateway address, allowing controlled communication between logical network segments.

---

## 🖥️ Server Infrastructure

Several servers are included in the simulation to represent common enterprise services.

### DNS Server

The DNS server provides name resolution for internal resources and can be used to associate hostnames with internal IP addresses.

### Web Server

A web server is configured to host an internal company website.

The project demonstrates how users from different branches can access centralized web resources across the routed enterprise network.

### DHCP Services

DHCP services are used to automate IP address assignment for supported client networks.

### File / Application Services

Additional servers can be used to represent centralized file, application, inventory, or organizational services.

---

## ☎️ VoIP

IP phones are included to demonstrate voice communication over the enterprise IP infrastructure.

The VoIP component provides an example of how voice devices can operate alongside normal data traffic within a converged network environment.

VLAN-based segmentation can be extended to provide dedicated voice networks in a larger implementation.

---

## ☁️ Cloud Connectivity

A cloud device and DSL modem are included to represent external or remote connectivity.

The cloud component demonstrates how a branch can connect to external resources while remaining part of the overall enterprise topology.

This can be extended to model:

* Internet connectivity
* Remote branch access
* External services
* WAN/ISP connectivity

---

## 🔐 Network Security Concepts

Although this is primarily a simulation and learning project, several security concepts are demonstrated:

* VLAN-based network segmentation
* WPA2-PSK wireless authentication
* Centralized WLC management
* Separate departmental networks
* Controlled inter-network communication
* Dedicated server networks
* Logical separation of users and infrastructure

For production environments, additional controls such as ACLs, SSH, port security, AAA, firewall policies, secure management VLANs, and stronger wireless authentication should be implemented.

---

## 🛠️ Technologies Demonstrated

This project brings together several Cisco networking concepts:

```text
Cisco Packet Tracer
        │
        ├── VLAN
        ├── Inter-VLAN Routing
        ├── DHCP
        ├── RIPv2
        ├── OSPF
        ├── Route Redistribution
        ├── Wireless LAN
        ├── WLC
        ├── WPA2-PSK
        ├── VoIP
        ├── DNS
        ├── Web Services
        ├── WAN Connectivity
        └── Cloud Integration
```

---

## 🧪 Testing the Topology

After opening the Packet Tracer project, the following tests can be performed.

### 1. Local Connectivity

Verify that devices can reach their default gateway:

```text
PC → Switch → Router Gateway
```

### 2. Inter-VLAN Connectivity

Test communication between devices belonging to different VLANs.

### 3. Branch-to-Branch Connectivity

Verify communication between:

```text
Store ↔ Warehouse
Store ↔ IT
Factory ↔ Administration
Warehouse ↔ Distribution Center
IT ↔ Distribution Center
```

### 4. Routing Verification

Useful Cisco commands include:

```bash
show ip route
show ip interface brief
show ip protocols
show running-config
show vlan brief
show interfaces trunk
```

For OSPF:

```bash
show ip ospf neighbor
show ip ospf interface
```

For RIPv2:

```bash
show ip route rip
```

### 5. Wireless Testing

Connect wireless clients to the configured SSIDs and verify:

* Authentication
* DHCP address assignment
* Default gateway
* DNS resolution
* Access to internal resources

### 6. Server Testing

Verify access to DNS, web, DHCP, and other configured services from multiple branches.

---

## 📂 Project Structure

A recommended repository structure is:

```text
Enterprise-Multi-Branch-Network-Infrastructure/
│
├── README.md
├── Packet-Tracer/
│   └── Enterprise-Network.pkt
│
├── Documentation/
│   ├── Network-Design.pdf
│   ├── IP-Addressing.xlsx
│   └── Network-Topology.png
│
└── Screenshots/
    ├── Topology.png
    ├── VLAN-Configuration.png
    ├── Routing.png
    └── Wireless-Configuration.png
```

---

## 💻 Requirements

To reproduce the simulation, install:

* **Cisco Packet Tracer**
* A computer capable of running the Packet Tracer application
* The project `.pkt` file

A modern desktop or laptop with at least **4 GB RAM** is recommended.

---

## 🚀 How to Run

1. Install Cisco Packet Tracer.
2. Clone or download this repository.
3. Open the `.pkt` project file.
4. Wait for the topology to load.
5. Inspect the routers, switches, servers, and end devices.
6. Test connectivity using the Packet Tracer simulation tools.
7. Use the CLI to inspect and modify configurations.

---

## 🎯 Learning Objectives

This project can be used to practice:

* Enterprise network design
* IP addressing and subnetting
* VLAN planning
* Inter-VLAN routing
* Dynamic routing
* OSPF configuration
* RIPv2 configuration
* Route redistribution
* DHCP deployment
* Wireless networking
* WLC configuration
* Server deployment
* VoIP networking
* WAN connectivity
* Network troubleshooting

---

## 📊 Project Highlights

| Component          | Implementation              |
| ------------------ | --------------------------- |
| Branches           | 6                           |
| Routers            | 6                           |
| Switches           | 6                           |
| PCs                | 15                          |
| Laptops            | 15                          |
| Smartphones        | 5                           |
| Tablets            | 3                           |
| IP Phones          | 2                           |
| Printers           | 5                           |
| Servers            | 4                           |
| WLC                | 2                           |
| Lightweight APs    | 2                           |
| Access Points      | 3                           |
| Routing            | RIPv2 + OSPF                |
| VLANs              | Multiple departmental VLANs |
| DHCP               | Enabled                     |
| Wireless Security  | WPA2-PSK                    |
| VoIP               | Included                    |
| DNS/Web Services   | Included                    |
| Cloud Connectivity | Included                    |

---

## 🔧 Troubleshooting

### Devices cannot communicate

Check:

```bash
show ip interface brief
show ip route
```

Verify that interfaces are enabled and that the correct routes exist.

### VLAN communication fails

Check:

```bash
show vlan brief
show interfaces trunk
```

Verify VLAN membership, trunk configuration, and gateway configuration.

### DHCP is not working

Verify:

* DHCP pool configuration
* Default gateway
* VLAN assignment
* Router/subinterface configuration
* DHCP server reachability

### OSPF routes are missing

Check:

```bash
show ip ospf neighbor
show ip route ospf
```

Verify that the correct interfaces are participating in OSPF.

### Wireless clients cannot connect

Verify:

* SSID
* WPA2-PSK configuration
* WLC configuration
* AP association
* DHCP availability
* Default gateway

---

## ⚠️ Important Note

This repository is intended primarily for **educational purposes, network simulation, and Cisco networking practice**.

The topology and configurations can be modified to experiment with different routing protocols, VLAN structures, addressing schemes, security policies, and enterprise services.

Credentials included in a lab configuration should **not** be reused in production environments.

---

## 👨‍💻 Project Purpose

The goal of this project is to demonstrate how a multi-location organization can build a structured network where users, servers, wireless devices, voice services, and branch offices communicate through a common enterprise infrastructure.

It provides a practical environment for understanding how individual networking technologies work together as a complete enterprise solution.

---

## ⭐ Future Improvements

Possible extensions include:

* 🔐 ACL-based traffic filtering
* 🛡️ Firewall integration
* 🔑 SSH-based device management
* 🔒 Port security
* 🧑‍💼 AAA authentication
* 📶 WPA3 / enterprise wireless security
* 🌐 Internet/NAT configuration
* 📈 Network monitoring
* 🗄️ Centralized backup services
* 🔄 Greater WAN redundancy
* ⚙️ More advanced OSPF areas
* 🧩 Network automation

---

## 📜 License

This project is provided for educational and networking practice purposes. Modify and extend the topology according to your learning or project requirements.
