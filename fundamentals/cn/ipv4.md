# IPv4

**Rule 1:** 32 bits address and into 4 octates
- 8bit.8bit.8bit.8bit

**Rule 2:** Each and every octate range from 0 - 255
- 8 bit each
  
**Rule 3:** IPv4 divided into 5 diffrent classes
- Class A => 0 - 128
- Class B => 129 - 191
- Class C => 192 - 223
- Class D => 224 - 239
- Class E => 240 - 255

**Rule 4:** First octate of IP address always define the class

**Rule 5:** We can only use Class A, Class B, Class C IP address while Class D used for multicasting and Class E used for R&D

**Rule 6:** Each and every class having an unique subnet-mask
- Class A : 255.0.0.0
- Class B : 255.255.0.0
- Class C : 255.255.255.0
- Class D : Not Applicable
- Class E : Not applicable

- Subnet mask:
  - **Network Id:** 255 part in class of subnet mask
  - **Host Id:** 0 part in class of subnet mask
  - Eg1: **10.0.0.1** => Network Id: 10 & Host Id: 0.0.0
  - Eg2: **192.168.1.1** => Network Id: 192.168.1 & Host Id: 1

**Rule 7:** To create a network network Id should be always same and host Id should be always different
- Network 1
  - 10.0.0.1
  - 10.0.1.0
  - 10.1.1.0
  - 10.0.0.2
- Network 2
  - 172.16.0.1
  - 172.16.0.2
  - 172.16.0.3
- Network 1 and Network 2 are different network as have different Network Id

**Rule 8:** How to define address
- In first octate you can't define 0 because network is not start with 0 
- Can't define 127 as it is loop back address to check self LAN Card
- Can define range between 1 - 223 
- Can't use range between 224 - 255 as they are reserved
- Can't use first Ip eg 10.0.0.0 because it represent complete network 
- Can't assign Ip eg 10.255.255.255 because it represent broadcast address of network

**Rule 9:** Maximum number of Ip Address in one network of any class 
- **Note:** remove 0 & 255 ip network and broadcast Ip respectivly
- Class C : (256-2) = 254
- Class B : ((256 * 256) - 2) = 65,534 
- Class A : ((256 * 256 * 256) - 2) = 1,67,77,214

**Rule 10:** Private Ip vs Public Ip
- **Private Ip**
  - Free
  - Use in LAN
  - Can access in LAN
  - Non-routable
  - Class A : 10.0.0.0 - 10.255.255.255
  - Class B : 172.16.0.0 - 172.31.255.255
  - Class C : 192.168.0.0 - 192.168.255.255
  - APIPA : 169.254.0.0 - 169.254.255.254
- **Public Ip**
  - Paid
  - Use in WAN
  - Can access anywhere through internet
  - Routable 
  - Apart from private Ip range of diffrent class



