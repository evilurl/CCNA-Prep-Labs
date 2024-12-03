# Basic Security Device Configuration Lab

This lab demonstrates basic security configurations on a router and switch, focusing on hostname changes, password configurations, and encrypting sensitive data. Below are the detailed steps for configuring the devices.

## Topology

The lab setup includes:
- A router (**R1**)
- A switch (**SW1**)
- 3 PCs (**PC1**, **PC2**, **PC3**)

## Objectives

**1.** Change the hostnames of the router and switch to the appropriate names (`R1`, `SW1`).

**2.** Configure an unencrypted enable password `CCNA` on both devices.

**3.** Test the unencrypted password by returning to user EXEC mode and re-entering privileged EXEC mode.

**4.** View the password in the running configuration.

**5.** Encrypt all current and future passwords on the devices.

**6.** Confirm that the passwords are encrypted in the running configuration.

**7.** Configure a more secure encrypted enable password `Cisco` on both devices.

**8.** Test the `Cisco` password by returning to privileged EXEC mode.

**9.** Examine the encryption type used for the enable password and enable secret in the running configuration.

**10.** Save the running configuration to the startup configuration.

## Commands and Configuration Steps

### Step 1: Change Hostnames
Use the `hostname` command in global configuration mode:
```bash
# On R1:
enable
configure terminal
hostname R1

# On SW1:
enable
configure terminal
hostname SW1
```

### Step 2: Configure Unencrypted Enable Password
Set the unencrypted password `CCNA`:
```bash
# On both devices:
enable
configure terminal
enable password CCNA
```

### Step 3: Test Unencrypted Password
**1.** Exit to user EXEC mode:
```bash
exit
```

**2.** Re-enter privileged EXEC mode using the password `CCNA`:
```bash
enable
```
Enter `CCNA` when prompted.

### Step 4: View Password in Running Configuration
Display the running configuration to view the unencrypted password:
```bash
show running-config
```

### Step 5: Encrypt All Passwords
Encrypt all current and future passwords:
```bash
# On both devices:
enable
configure terminal
service password-encryption
```

### Step 6: Confirm Password Encryption
Verify that passwords are now encrypted:
```bash
show running-config
```

### Step 7: Configure Encrypted Enable Password
Set a more secure encrypted enable password `Cisco`:

```bash
# On both devices:
enable
configure terminal
enable secret Cisco
```

### Step 8: Test the Encrypted Password
**1.** Exit to user EXEC mode:
```bash
exit
```

**2.** Re-enter privileged EXEC mode using the password `Cisco`:
```bash
enable
```

Enter `Cisco` when prompted.

### Step 9: Examine Password Encryption Types
Inspect the encryption types used:
```bash
show running-config
```

- Enable password: Typically Type 7 (weak encryption).
- Enable secret: Type 5 (MD5 hashing).

### Step 10: Save Configuration
Save the running configuration to the startup configuration:
```bash
copy running-config startup-config
```

### Key Notes
- The `enable password` is visible in plain text unless encryption is enabled using `service password-encryption`.
- The `enable secret` is always encrypted and takes precedence over `enable password`.

### Conclusion
This lab covers fundamental security configurations to ensure device access is secure and passwords are encrypted.
