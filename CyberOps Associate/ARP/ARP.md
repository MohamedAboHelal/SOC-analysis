- MAC addresses: These addresses are used to deliver the data link frame with the encapsulated IP packet from one NIC to another NIC on the same network. If the destination IP address is on the same network, the destination MAC address will be that of the destination device.
- The default gateway address is the address of the router’s NIC
- How are the IPv4 addresses of the IPv4 packets in a data flow associated with the MAC addresses on each link along the path to the destination?             This is done through a process called Address Resolution Protocol (ARP).
- A device uses (ARP) to determine the destination MAC address of a local device when it knows its IPv4 address.
- ARP provides two basic functions:
  - Resolving IPv4 addresses to MAC addresses
  - Maintaining a table of IPv4 to MAC address mappings
- ARP request is:  sent when a device needs to determine the MAC address that is associated with an IPv4 address, and it does not have an entry for the IPv4 address in its ARP table.



<img src="https://github.com/MohamedAboHelal/SOC-analysis/blob/main/CyberOps%20Associate/ARP/Mics/ARP_request.PNG" style="zoom:50%;" />



- Because ARP requests are broadcasts, they are flooded out all ports by the switch, except the receiving port. All Ethernet NICs on the LAN process broadcasts and must deliver the ARP request to its operating system for processing. Every device must process the ARP request to see if the target IPv4 address matches its own. A router will not forward broadcasts out other interfaces.
- newer Windows operating systems store ARP table entries between 15 and 45 seconds, as illustrated in the figure.
- **show ip arp**: On a Cisco router tnis is command is used to display the ARP table.
- **arp –a**: On a Windows this is command is used to display the ARP table.
- **arp -n   **:on linux this is command is used to display the ARP table
- **conclusion**: if you want to know the MAC of your modem -> use the command **arp -a** and scroll down till the ip of default getway, then the MAC that shown there is the MAC of the modem. 
- ARP poisoning attack: This is a technique used by a threat actor to reply to an ARP request for an IPv4 address that belongs to another device, such as the default gateway.The receiver of the ARP reply will add the wrong MAC address to its ARP table and send these packets to the threat actor.
- **Enterprise level switches include mitigation techniques known as *`dynamic ARP inspection (DAI)`*. **
- **Dynamic ARP Inspection** (**DAI**): is a security feature in MS switches that protects networks against man-in-the-middle **ARP** spoofing attacks. **DAI** inspects Address Resolution Protocol (**ARP**) packets on the LAN and uses the information in the **DHCP snooping** table on the switch to validate **ARP** packets.
- **If you want to execute ARP poisoning attack:**
  - first know the MAC of the default getway as we mentioned above
  - then spoof your MAC  to the MAC of the default getway
  - finally use a sniffer like (wrieshark) to sniff all traffics in the network
