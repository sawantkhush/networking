# networking

Networking is about how data moves between systems — using packets, IP addresses, and routing. It covers the flow of information across devices, servers, and the internet, which is the foundation for communication and security.

# Create a Custom Packet with Scapy

Scapy → It is a powerful Python library used for network packet crafting, sending, sniffing, and analysis. It allows you to build custom packets at different protocol layers and interact with networks for testing, security research, and troubleshooting.

This script helps to understand how packets are built and transmitted.

● IP(dst=target_ip) – This creates the IP header and sets the destination address.

● ICMP(type=8) – The type=8 means “Echo Request” (the same as what the ping command sends

● packet = ip_layer / icmp_layer / custom_payload – The / operator is overloaded in Scapy. Instead of dividing, it means stacking protocol layers (bringing it under one roof). 

● send(packet) – This sends raw packets over the network, which usually requires administrator/root privileges.

Capture the packet with tcpdump/Wireshark to verify.
