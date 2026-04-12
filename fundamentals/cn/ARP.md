# Address Resolution Protocol (ARP)
- Maps logical IPv4 addresses (32-bit) to physical MAC addresses (48-bit) within a local area network (LAN)
-  Network layer <-Bridge-> data link layer
-  Maintaines ARP table [[ARP-table]]


**How it Works:** 
- When a device sends data, it checks its local "ARP cache" to see if the IP-to-MAC mapping is already stored. 
- If not, a broadcast request is sent, and the target replies directly (unicast) with its MAC address.
  
**Packet Format:** 
- Hardware type
- protocol type
- hardware address length
- protocol address length
- operation code (request/reply)
- source/destination addresses.

**Limitations:**
- ARP is primarily for IPv4. 
- IPv6 networks use the Neighbor Discovery Protocol (NDP)