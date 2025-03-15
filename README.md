<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
This setup begins by creating a Virtual Network and a Subnet in Azure, followed by deploying two virtual machines—Windows 10 and Linux (Ubuntu)—within the same network to ensure they can communicate with each other. Using Wireshark on the Windows 10 VM, you filter and observe various network traffic types, such as ICMP when pinging the Ubuntu VM, SSH traffic when accessing the Ubuntu VM via private IP, DHCP traffic when issuing a new IP address through PowerShell, and DNS traffic when using nslookup to resolve domains like google.com and disney.com. You also configure a Network Security Group (NSG) to disable and enable ICMP traffic, observing its effects on network communication in Wireshark. Additionally, you filter RDP traffic to observe continuous connections on the Windows 10 VM. This setup provides hands-on experience with network traffic analysis, firewall configuration, and VM communication within a virtualized environment.<br />


<h2>Video Demonstration</h2>

https://www.youtube.com/channel/UCjL4Qz0Mm7CG9trg-1v4lgQ

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

1. Create a Virtual Network and Subnet

2. Create Windows 10 and Linux (Ubuntu)  Virtual Machines and join them to the same V-net

3. Login to Windows 10 (VM) and filter ICMP Traffic using Wireshark

4. Inside Windows 10 (VM), ping the Ubuntu (VM) private IP address and observe ping requests and replies within Wireshark.

5. Inside Windows 10 (VM), use PowerShell and ping a public website (Eg:www.google.com) and observe the traffic in Wireshark

6. Configure a Firewall [Network Security Group] by disabling and enabling ICMP traffic and observe ICMP traffic activities in Wireshark

7. From Windows 10 VM, “SSH into” Ubuntu Virtual Machine (via its private IP address) and observe SSH Traffic in Wireshark

8. From Windows 10 VM, attempt to issue your VM a new IP address with PowerShell and Observe DHCP Traffic in Wireshark

9. From Windows 10 VM, inside PowerShell, use nslookup to see the IP addresses of google.com and disney.com, and observe DNS Traffic in Wireshark

10. From Windows 10 VM, Inside Wireshark, filter for RDP traffic (tcp.port == 3389) and observe the immediate non-stop spam of traffic.


<h2>Actions and Observations</h2>

<h2>Create a Virtual Network and Subnet</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A Virtual Network (VNet) is created to establish a private networking environment in which virtual machines and other resources can communicate securely. Within this VNet, a Subnet is configured to segment the network, allowing efficient traffic management and security control. The subnet assigns IP addresses to the connected virtual machines and ensures they can communicate with each other while also being managed through network security rules. This setup forms the foundation for networking in the cloud, enabling virtual machines to interact while maintaining isolation from external networks unless explicitly configured.
</p>
<br />

<h2>Create Windows 10 and Linux (Ubuntu)  Virtual Machines and join them to the same V-net</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A Windows 10 and a Linux (Ubuntu) virtual machine are deployed and configured to connect to the same Virtual Network (VNet), ensuring they can communicate securely within a shared private network. By being in the same VNet, both VMs can exchange data without needing external internet access, allowing for seamless interaction, such as file transfers, remote connections, and network-based services. This setup is essential for testing, development, and learning environments where cross-platform connectivity and network traffic analysis are required
</p>
<br />

<h2>Login to Windows 10 (VM) and filter ICMP Traffic using Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I log into the Windows 10 virtual machine, launch Wireshark, and apply a filter to specifically capture and analyze ICMP (Internet Control Message Protocol) traffic, which is used for network diagnostics, such as ping requests and replies. This allows me to monitor real-time network communication, observe how ICMP packets are transmitted and received, and troubleshoot connectivity issues between devices within the Virtual Network (VNet). By filtering ICMP traffic, i can isolate ping-related network activity and gain insights into how packets flow between the Windows 10 and Ubuntu virtual machines.
</p>
<br />

<h2>Inside Windows 10 (VM), ping the Ubuntu (VM) private IP address and observe ping requests and replies within Wireshark.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I open a command prompt and use the ping command to send ICMP echo requests to the Ubuntu VM's private IP address. Simultaneously, Wireshark is used to capture and analyze the network traffic, allowing me to observe the ICMP request and reply packets exchanged between the two machines. This process verifies that both VMs can communicate within the Virtual Network (VNet) and helps analyze the response time, packet flow, and potential network issues. It also provides insights into how ICMP traffic behaves in a controlled network environment.
</p>
<br />

<h2>Inside Windows 10 (VM), use PowerShell and ping a public website (Eg:www.google.com) and observe the traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I open PowerShell and use the ping command to send ICMP echo requests to a public website such as www.google.com. Meanwhile, Wireshark is running to capture and analyze the network traffic, allowing me to observe how the request is processed. This includes DNS resolution (translating the domain name into an IP address) and the ICMP request-reply exchanges between my VM and the public server. This step helps analyze how network traffic flows between a private virtual machine and an external internet destination, providing insights into latency, packet loss, and firewall behavior within the network.
</p>
<br />

<h2>Configure a Firewall [Network Security Group] by disabling and enabling ICMP traffic and observe ICMP traffic activities in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, i configure a Network Security Group (NSG) in Azure to control the flow of ICMP traffic by initially disabling it, preventing ping requests and replies from passing through the network. Afterward, i enable ICMP traffic again, allowing the communication to resume. While these changes are made, Wireshark is used to capture and analyze the network traffic, allowing you to observe how the ICMP packets are affected by the firewall settings. This process helps demonstrate the impact of firewall rules on network connectivity and shows how enabling or disabling specific traffic types like ICMP can control communication between virtual machines.
</p>
<br />

<h2>From Windows 10 VM, “SSH into” Ubuntu Virtual Machine (via its private IP address) and observe SSH Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I use an SSH client to establish a secure connection to the Ubuntu VM by specifying its private IP address. As the connection is initiated, Wireshark is used to capture and analyze the network traffic, focusing on the SSH handshake and the encrypted communication between the two machines. This process allows me to observe the protocol in action, including the exchange of keys, authentication steps, and the establishment of a secure channel for remote management, all while monitoring the underlying network packets.
</p>
<br />

<h2>From Windows 10 VM, attempt to issue your VM a new IP address with PowerShell and Observe DHCP Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I use PowerShell to initiate a DHCP request to obtain a new IP address from the network’s DHCP server. Wireshark is used to capture and analyze the DHCP traffic, which includes the DHCP Discover, Offer, Request, and Acknowledge (DORA) process. This allows me to observe the communication between the VM and the DHCP server as the new IP address is assigned, including the exchange of DHCP packets that handle IP address allocation and configuration settings for the Windows 10 VM.
</p>
<br />

<h2>From Windows 10 VM, inside PowerShell, use nslookup to see the IP addresses of google.com and disney.com, and observe DNS Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I open PowerShell and use the nslookup command to query the DNS server for the IP addresses of google.com and disney.com. Wireshark is used to capture and analyze the DNS traffic generated during this process, which includes the DNS query sent by the Windows VM and the DNS response from the server containing the resolved IP addresses. This allows me to observe the DNS protocol in action, including the communication between the VM and the DNS server, and analyze the response times, packet details, and potential issues in the DNS resolution process.
</p>
<br />

<h2>From Windows 10 VM, Inside Wireshark, filter for RDP traffic (tcp.port == 3389) and observe the immediate non-stop spam of traffic.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I apply a Wireshark filter for RDP (Remote Desktop Protocol) traffic using tcp.port == 3389, which isolates the packets associated with RDP connections. This reveals a constant flow of traffic, which could include multiple connection attempts, session negotiations, or ongoing communication over the RDP protocol. By observing this traffic, I can analyze the behavior of RDP sessions, such as authentication attempts, the exchange of data between the client and server, and any potential issues like unauthorized access attempts or network performance concerns.
</p>
<br />
