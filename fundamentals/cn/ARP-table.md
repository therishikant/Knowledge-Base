# Address Resolution Protocol (ARP) Table
- Dynamic database in networking devices that maps local IPv4 addresses to physical MAC addresses
- Eliminating the need to constantly re-broadcast "who-has" requests for known devices
- Uses ARP [[ARP]] for automatic update of table.

**Purpose:** 
- Maps Network Layer (IP) addresses to Link Layer (MAC) addresses, enabling communication within a broadcast domain
  
**Location:** 
- Maintained on computers, routers, and switches

**Cache Timeout:** 
- Entries are not permanent. 
- They are removed after a certain time (e.g., 240 minutes in some systems)

**Commands:** 
- arp -a (view) 
- arp -d (delete)
- arp -s (add static)

**ARP Table Structure**
- IP Address: The network address.
- MAC Address: The corresponding hardware address.
- Interface: The network interface card (NIC) used to reach the device.
- Type: Whether the entry is static or dynamic. 