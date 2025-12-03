## Ubuntu Setup

### Specs
- **Host Machine:** MacBook Air M2  
- **OS:** macOS 15.4.1  
- **VM Software:** UTM 
- **VM Specs:** 3 GB RAM, 8 GB Storage, Bridged Network  
- **VM IP Address:** 192.168.0.137  
- **Host IP Address:** 192.168.0.224  
- **Ubuntu Version:** 24.04.3 ARM64  

> Birdged Network allows the VM and host to be on the same network, allowing access from other network devices.
------

### Ubuntu Server Installation

1. Download Ubuntu Server ARM64 ISO:  
   [https://ubuntu.com/download/server](https://ubuntu.com/download/server)
2. Create a new VM in UTM with **bridged networking**.
3. Perform **Standard Installation** with **OpenSSH Server** enabled.
4. Reboot and remove the ISO.
5. Log in to the newly installed Ubuntu system.

------