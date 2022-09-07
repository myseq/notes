# IPv6 #
https://www.youtube.com/watch?v=oItwDXraK1M

### Address length and format ###
- IPv6 uses **128 bits** or **(16 bytes)** 
- IPv6 is written in **8 groups of 2 bytes** in hex and separated by colon :
- Example:

    FDDD:F00D:CAFE:0000:0000:0000:0000:0001

- Leading zeros of each block can be omitted, the above address can hence be written like this:

    FDDD:F00D:CAFE:0:0:0:0:1

- We can abbreviate whole blocks of zeros with `::` and write:

    FDDD:F00D:CAFE::1

- This can only be done *once* in order to void ambiguity:

    FF:0:0:0:1:0:0:1 (correct)
    FF::1:0:0:1 (correct)
    FF:0:0:0:1::1 (correct)
    FF::1::1 (ambiguous, wrong)


### Protocols ###

| Number | Protocol  | Purpose                                   |
| ------ | --------- | ----------------------------------------- |
|  1     | ICMPv6    | Information, Error reporting, diagnostics |
|  6     | TCPv6     | Stateful - controls if packets arrived    |
| 17     | UDPv6     | Stateless - streaming applications etc.   |


### Ways to  assign IPv6 addresses ###

> **Static** - fixed address  
> **SLAAC** - Stateless Address Autoconfiguration (host generates itself)  
> **DHCPv6** - Dynamic host configuration protocol (assigned by central server)  


### Scopes and special addresses ###

**GLOBAL** - everything (i.e. the whole internet)  
**UNIQUE LOCAL** - everything in our LAN (behind the internet gateway)  
**LINK LOCAL** - (will never be routed, valid in one collision domain, i.e. on the same switch)  
**LOCALHOST** - same machine


| Range | CIDR    | Purpose                                        |
| ----- | --------- | ---------------------------------------------- |
| | ::1/128   | Loopback address (localhost)                   |
| | ::/128    | unspecified address                            |
| 2000:0000:0000:0000:0000:0000:0000:0000 ~ 3fff:ffff:ffff:ffff:ffff:ffff:ffff:ffff | 2000::/3  | GLOBAL unicast (Internet)          |
| FC00:0000:0000:0000:0000:0000:0000:0000 ~ FDFF:ffff:ffff:ffff:ffff:ffff:ffff:ffff | FC00::/7  | Unique-local (LAN)                 |
| FE80:0000:0000:0000:0000:0000:0000:0000 ~ FEBF:ffff:ffff:ffff:ffff:ffff:ffff:ffff | FE80::/10 | Link-Local Unicast (same switch)   |

- Always use the smallest possible scope for communication  
- A host can have **multiple** addresses in different scopes


### Subnetting ###

- First 48 bits: **Network** address
- Next 16 bits: **Subnet** address
  - Last 64 bits: **Device** address

**Network + Subnet = Prefix**

The following address

    2003:1000:1000:1600:1234::1

would have the network `2003:1000:1000`, the subnet `1600`, so together the prefix `2003:1000:1000:1600`. 

If the ISP provider **delegated** a part of the prefix to me (e.g. `2003:1000:1000:1600/56`) then I could use the subnets `2003:1000:1000:1600` `2003:1000:1000:16FF` for my own purposes (i.e. define 256 subnets in this example)


### Using IPv6 addresses in browser ###

IPv6 addresses can be written in brackets in order to be identified as IPv6, e.g. `https://[2a00:1450:4001:82a::2004]` (might lead to a certificate error though with https as the hostname can not be verified against the certificate)
