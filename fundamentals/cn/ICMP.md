# The Internet Control Message Protocol (ICMP) 
- Network layer protocol used by devices like routers and hosts to send error messages and operational information
- It supports IP by reporting issues like unreachable hosts or packet fragmentation

**Purpose:** 
- Troubleshooting
- Error reporting
- Network diagnostics

**Common Uses:** 
- ping (echo request/reply)
- traceroute to test connection connectivity and speed.

**Security Risk:** 
- DDoS attacks

**Message Structure:** 
- ICMP packets are encapsulated within IP packets
- featuring a 64-bit header containing Type, Code, and Checksum fields.

**Common ICMP Types (RFC 792):**
- Type 0: Echo Reply
- Type 3: Destination Unreachable
- Type 8: Echo Request
- Type 11: Time Exceeded