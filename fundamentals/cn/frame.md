# Frame 
- A frame is the basic unit of data transmission at the Data Link Layer (Layer 2)
-  encapsulating network packets with control information for local delivery
-  

**Encapsulation:** 
- The Data Link Layer adds a header (source/destination MAC addresses) and a trailer to the network layer packet

**Addressing:** 
- Uses MAC addresses for moving data within the same local network (LAN)

**Frame Structure:**
- **Header:** 
  - Preamble
  - Start of Frame (SOF) delimiter
  - Destination MAC Address
  - Source MAC Address
  - Type/Length field

- **Payload:** 
  - The data packet (typically 46-1500 bytes in Ethernet) being transported

- **Trailer:** 
  - Frame Check Sequence (FCS) for error checking