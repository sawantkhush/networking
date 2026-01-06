# networking

Networking is about how data moves between systems — using packets, IP addresses, and routing. It covers the flow of information across devices, servers, and the internet, which is the foundation for communication and security.

## Create a Custom Packet with Scapy

Scapy → It is a powerful Python library used for network packet crafting, sending, sniffing, and analysis. It allows you to build custom packets at different protocol layers and interact with networks for testing, security research, and troubleshooting.

This script helps to understand how packets are built and transmitted.

● IP(dst=target_ip) – This creates the IP header and sets the destination address.

● ICMP(type=8) – The type=8 means “Echo Request” (the same as what the ping command sends

● packet = ip_layer / icmp_layer / custom_payload – The / operator is overloaded in Scapy. Instead of dividing, it means stacking protocol layers (bringing it under one roof). 

● send(packet) – This sends raw packets over the network, which usually requires administrator/root privileges.

Capture the packet with tcpdump/Wireshark to verify.

## Create a python based basic port scanner
Port Scanning is used to discover open or closed ports in the network, be it of any protocol as TCP or UDP

It is also important to mention which protocol we are referring to scan TCP : Connection-oriented and UDP : Connectionless

Python do not provide a direct library for such we could use socket library, that provides low-level access to TCP and UDP communication, which is why it is used. Higher-level tools like Nmap or Scapy internally rely on the same networking mechanisms.

This script creates a basic python based port scanning, some tips to remember are as follows :
● for port in range(1,40): - here define the range of port to be scanned it can be any for faster or demo, testing purpose it is recommneded to scan a short range for the same

● s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) - this is other very important line of code let's breakdown 

socket.socket is the constructor here creating an object

socket.AF_INET - here it defines Adress Family IPv4 if we want IPv6 we could simply change it to --- socket.AF_INET6

socket.SOCK_STREAM - defines socket type i.e. TCP if we want UDP use  --- socket.SOCK_DGRAM

●  s.settimeout(0.5) - set a time out for the ports to scan it is necessary if time is not set it would get stuck forever in scanning and hangs the system

●  s.connect_ex((target,port)) == 0: - here s.connect_ex is a built-in function of socket, it tries to connect, returns 0 if success, error code if failure — no exceptions.
if we had to simply use connect() it would try to connect, raise exception if connection fails.

lastly close the port
