# Network Protocol Notes: The Ping Command

## 1. Overview
*   **Definition**: A network utility used to test the reachability of a host on an IP network.
*   **Core Protocol**: Uses **ICMP** (Internet Control Message Protocol).
*   **Key Metric**: Measures **Round-Trip Time (RTT)** in milliseconds (ms).

---

## 2. The Layer-by-Layer Process (OSI Model)

### Layer 7: Application Layer
*   **Action**: User executes `ping <hostname>`.
*   **Process**: If a hostname (like `google.com`) is used, the system performs a **DNS Lookup** to find the destination IP address.

### Layer 4: Transport Layer
*   **Note**: Ping **skips** TCP/UDP. It interacts directly with Layer 3 using "raw sockets." No port numbers are used.

### Layer 3: Network Layer (The Core)
*   **Encapsulation**: The ICMP message is placed into an **IP Datagram**.
*   **Addressing**: Source and Destination IP addresses are attached.
*   **TTL (Time to Live)**: A value (e.g., 64 or 128) is set. Each router the packet passes through decreases this by 1. If it hits 0, the packet is discarded to prevent infinite loops.

### Layer 2: Data Link Layer
*   **Framing**: The IP datagram is wrapped into an **Ethernet Frame**.
*   **Addressing**: Source and Destination **MAC addresses** are attached.
*   **ARP (Address Resolution Protocol)**: If the MAC address of the next hop (router) isn't known, an ARP request is sent first to find it.

### Layer 1: Physical Layer
*   **Transmission**: Data is converted into bits (1s and 0s) and sent as electrical, optical, or radio signals across the physical medium (Copper, Fiber, or Wi-Fi).

---

## 4. Key Troubleshooting Indicators
*   **Request Timed Out**: The destination is down, a firewall is blocking ICMP, or the return path is broken.
*   **Destination Host Unreachable**: The local router doesn't know how to get to the target network.
*   **High Latency**: Indicates network congestion or physical distance issues.
*   **Packet Loss**: Indicates a faulty cable, interference, or an overloaded network device.

## 5. Resources
- [[ARP-table]]
- [[ICMP]]