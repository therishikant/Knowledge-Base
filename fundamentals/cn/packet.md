# Packet
- A small, formatted unit of data—consisting of a header (control information) and payload (actual data)—sent over a network
- Created at layer 3
- Uses IP addresses to move data 

**Packet Structure**
- **Header:** 
  - Source IP 
  - Destination IP 
  - packet sequence number
  - protocol information
  
- **Payload:** 
  - The actual, raw data being transmitted.

- **Footer/Trailer:** 
  - Contains bits that inform the receiver that the packet is complete and sometimes holds error-checking codes (like a checksum).
