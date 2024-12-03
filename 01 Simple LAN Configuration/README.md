# Simple LAN Configuration Lab

This lab demonstrates a basic LAN setup where three PCs are connected via a switch. The lab includes basic security configurations for the router and switch, focusing on hostname changes, password configurations, and securing sensitive data.

---

## Topology

- **Devices**:
  - Router: R1
  - Switch: SW1
  - PCs: PC1, PC2, PC3
- **Connections**:
  - PC1, PC2, and PC3 are connected to SW1.
  - SW1 is connected to R1.

---

## Objectives

1. **Configure Hostnames**: Change the hostname of the router and switch to `R1` and `SW1`, respectively.
2. **Set Enable Passwords**: Configure unencrypted and encrypted passwords for device access.
3. **Test Access**: Verify password functionality and user access to the devices.
4. **Encrypt Passwords**: Ensure all passwords are encrypted for added security.
5. **Save Configuration**: Save the running configuration to startup configuration.

---

## Configuration Steps

### Step 1: Change Hostnames
1. Access the router and switch CLI.
2. Enter global configuration mode:
   ```bash
   # On R1:
   enable
   configure terminal
   hostname R1

   # On SW1:
   enable
   configure terminal
   hostname SW1
