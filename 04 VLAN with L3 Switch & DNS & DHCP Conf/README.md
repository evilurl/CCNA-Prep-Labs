# VLAN Configuration Lab

This lab demonstrates the setup and configuration of VLANs in a network using Cisco Packet Tracer. It involves multiple VLANs, inter-switch connectivity, and basic security configurations.

---

## Topology

- **Devices**:
  - Layer 3 Switch: Cisco 3700
  - Layer 2 Switch: Cisco 2960
  - PCs: PC1, PC2, PC3
  - Server: DNS/DHCP Server
- **Connections**:
  - PC1, PC2, and PC3 are connected to the Cisco 2960 switch.
  - The Cisco 2960 switch is connected to the Cisco 3700 switch via a trunk link.
  - A DNS/DHCP server is connected to the Cisco 3700 switch.

---

## Objectives

1. **Configure VLANs**: Create four VLANs:
   - VLAN 10: **PC1**
   - VLAN 20: **PC2**
   - VLAN 30: **PC3**
   - VLAN 100: Reserved for management.
2. **Set Access Ports**: Configure each PC to be part of its respective VLAN.
3. **Establish Trunk Link**: Connect the Cisco 2960 switch to the Cisco 3700 switch using a trunk link.
4. **Assign IPs**:
   - Assign `192.168.100.2` to the Cisco 2960 switch.
   - Assign `192.168.100.1` to the Cisco 3700 switch.
   - Configure the following SVI IP addresses:
     - VLAN 10: `192.168.10.1/24`
     - VLAN 20: `192.168.20.1/24`
     - VLAN 30: `192.168.30.1/24`
     - VLAN 100: `192.168.100.1/24`
5. **Configure SSH**: Enable SSH on both switches for secure management.
6. **Integrate DNS/DHCP Server**:
   - Configure DHCP to provide IP addresses to the PCs.
   - Configure the DNS server with appropriate records.
7. **Ensure Connectivity**: All PCs should be able to ping each other.

---

## Configuration Steps

### Step 1: Create VLANs
1. On the Cisco 2960 switch:
   ```bash
   enable
   configure terminal
   vlan 10
   name VLAN10
   vlan 20
   name VLAN20
   vlan 30
   name VLAN30
   vlan 100
   name VLAN100
   exit
   ```
2. Assign access ports for each PC:
   ```bash
   interface FastEthernet0/1
   switchport mode access
   switchport access vlan 10
   exit
   interface FastEthernet0/2
   switchport mode access
   switchport access vlan 20
   exit
   interface FastEthernet0/3
   switchport mode access
   switchport access vlan 30
   exit
   ```

### Step 2: Configure Trunk Link
1. On the Cisco 2960 switch:
   ```bash
   interface GigabitEthernet0/1
   switchport trunk encapsulation dot1q
   switchport mode trunk
   exit
   ```
2. Repeat the trunk configuration on the Cisco 3700 switch.

### Step 3: Configure SVI IPs on Cisco 3700
1. Assign IPs to VLAN interfaces:
   ```bash
   interface vlan 10
   ip address 192.168.10.1 255.255.255.0
   no shutdown
   exit
   interface vlan 20
   ip address 192.168.20.1 255.255.255.0
   no shutdown
   exit
   interface vlan 30
   ip address 192.168.30.1 255.255.255.0
   no shutdown
   exit
   interface vlan 100
   ip address 192.168.100.1 255.255.255.0
   no shutdown
   exit
   ```

### Step 4: Enable IP Routing
1. Enable IP routing:
   ```bash
    enable
    configure terminal
    ip routing
    exit
   ```

### Step 5: Configure SSH on Both Switches
1. Generate RSA keys:
   ```bash
   ip domain-name example.com
   crypto key generate rsa
   ```
2. Configure VTY lines:
   ```bash
   line vty 0 4
   transport input ssh
   login local
   exit
   ```

### Step 6: Configure DNS/DHCP Server
1. On the DHCP server:
   - Assign IP pools for each VLAN.
   - Set `192.168.100.1` as the default gateway.
2. On the DNS server:
   - Add appropriate records for hostname resolution.

### Step 7: Test Connectivity
- Ping between PCs to ensure communication.
- Verify DNS resolution from PCs.

---

## Tools Used

- **Packet Tracer**: The `.pkt` file is included in the repository for use.
- **Devices**:
  - Layer 2 Switch: Cisco 2960
  - Layer 3 Switch: Cisco 3700
  - DNS/DHCP Server
  - PCs

---

## Lab File

The `.pkt` lab file is available in this repository:
- **[04. VLAN with DNS & DHCP Conf.pkt](04.%20VLAN%20with%20DNS%20&%20DHCP%20Conf.pkt)**

---

## Conclusion

This lab provides a hands-on exercise for configuring VLANs, trunking, and basic device management using Cisco Packet Tracer. By completing this lab, you'll gain practical knowledge of VLAN segmentation, inter-VLAN routing, and network device security.

---
