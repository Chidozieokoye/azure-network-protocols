<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this setup, I began by creating a Virtual Network and a Subnet in Azure, then deployed two virtual machines—Windows 10 and Linux (Ubuntu)—within the same network to ensure they could communicate with each other. Using Wireshark on the Windows 10 VM, I filtered and observed various types of network traffic. This included ICMP traffic when pinging the Ubuntu VM, SSH traffic when accessing the Ubuntu VM via its private IP, DHCP traffic when issuing a new IP address through PowerShell, and DNS traffic when using nslookup to resolve domains like google.com and disney.com. I also configured a Network Security Group (NSG) to disable and enable ICMP traffic and observed its effects on network communication in Wireshark. Additionally, I filtered RDP traffic to monitor continuous connections on the Windows 10 VM. This setup gave me hands-on experience with network traffic analysis, firewall configuration, and VM communication within a virtualized environment.<br />

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
In this step, I created a Virtual Network (VNet) to establish a private networking environment where virtual machines and other resources can communicate securely. Within the VNet, I configured a Subnet to segment the network, allowing for efficient traffic management and enhanced security control. The subnet assigns IP addresses to the connected virtual machines, ensuring they can communicate with each other while also being managed through network security rules. This setup forms the foundation for cloud networking, enabling virtual machines to interact while maintaining isolation from external networks unless specifically configured otherwise.
</p>
<br />

<h2>Create Windows 10 and Linux (Ubuntu)  Virtual Machines and join them to the same V-net</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I deployed a Windows 10 and a Linux (Ubuntu) virtual machine, configuring both to connect to the same Virtual Network (VNet). This ensures that the two VMs can communicate securely within a shared private network. By being in the same VNet, the VMs can exchange data without needing external internet access, allowing for seamless interaction like file transfers, remote connections, and network-based services. This setup is crucial for testing, development, and learning environments where cross-platform connectivity and network traffic analysis are necessary.
</p>
<br />

<h2>Login to Windows 10 (VM) and filter ICMP Traffic using Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I logged into the Windows 10 virtual machine, launched Wireshark, and applied a filter to specifically capture and analyze ICMP (Internet Control Message Protocol) traffic, which is used for network diagnostics like ping requests and replies. This allowed me to monitor real-time network communication, observe how ICMP packets are transmitted and received, and troubleshoot any connectivity issues between devices within the Virtual Network (VNet). By filtering ICMP traffic, I was able to isolate ping-related network activity and gain insights into how packets flow between the Windows 10 and Ubuntu virtual machines.
</p>
<br />

<h2>Inside Windows 10 (VM), ping the Ubuntu (VM) private IP address and observe ping requests and replies within Wireshark.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I opened a command prompt and used the ping command to send ICMP echo requests to the Ubuntu VM's private IP address. At the same time, I used Wireshark to capture and analyze the network traffic, allowing me to observe the ICMP request and reply packets exchanged between the two machines. This process verified that both VMs could communicate within the Virtual Network (VNet) and helped me analyze the response time, packet flow, and potential network issues. It also provided valuable insights into how ICMP traffic behaves in a controlled network environment.
</p>
<br />

<h2>Inside Windows 10 (VM), use PowerShell and ping a public website (Eg:www.google.com) and observe the traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I opened PowerShell and used the ping command to send ICMP echo requests to a public website, such as www.google.com. At the same time, I had Wireshark running to capture and analyze the network traffic, allowing me to observe how the request was processed. This included DNS resolution (translating the domain name into an IP address) and the ICMP request-reply exchanges between my VM and the public server. This step helped me analyze how network traffic flows between a private virtual machine and an external internet destination, providing valuable insights into latency, packet loss, and firewall behavior within the network.
</p>
<br />

<h2>Configure a Firewall [Network Security Group] by disabling and enabling ICMP traffic and observe ICMP traffic activities in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, I configured a Network Security Group (NSG) in Azure to control the flow of ICMP traffic by initially disabling it, preventing ping requests and replies from passing through the network. Afterward, I enabled ICMP traffic again, allowing the communication to resume. While making these changes, I used Wireshark to capture and analyze the network traffic, observing how the ICMP packets were affected by the firewall settings. This process helped demonstrate the impact of firewall rules on network connectivity and showed how enabling or disabling specific traffic types, like ICMP, can control communication between virtual machines.
</p>
<br />

<h2>From Windows 10 VM, “SSH into” Ubuntu Virtual Machine (via its private IP address) and observe SSH Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I used an SSH client to establish a secure connection to the Ubuntu VM by specifying its private IP address. As the connection was initiated, I ran Wireshark to capture and analyze the network traffic, focusing on the SSH handshake and the encrypted communication between the two machines. This process allowed me to observe the protocol in action, including the exchange of keys, authentication steps, and the establishment of a secure channel for remote management, all while monitoring the underlying network packets.
</p>
<br />

<h2>From Windows 10 VM, attempt to issue your VM a new IP address with PowerShell and Observe DHCP Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I used PowerShell to initiate a DHCP request to obtain a new IP address from the network’s DHCP server. At the same time, I ran Wireshark to capture and analyze the DHCP traffic, including the DHCP Discover, Offer, Request, and Acknowledge (DORA) process. This allowed me to observe the communication between the VM and the DHCP server as the new IP address was assigned, including the exchange of DHCP packets that handled the IP address allocation and configuration settings for the Windows 10 VM.
</p>
<br />

<h2>From Windows 10 VM, inside PowerShell, use nslookup to see the IP addresses of google.com and disney.com, and observe DNS Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I opened PowerShell and used the nslookup command to query the DNS server for the IP addresses of google.com and disney.com. I ran Wireshark to capture and analyze the DNS traffic generated during this process, which included the DNS query sent by the Windows VM and the DNS response from the server containing the resolved IP addresses. This allowed me to observe the DNS protocol in action, including the communication between the VM and the DNS server, and analyze the response times, packet details, and potential issues in the DNS resolution process.
</p>
<br />

<h2>From Windows 10 VM, Inside Wireshark, filter for RDP traffic (tcp.port == 3389) and observe the immediate non-stop spam of traffic.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 virtual machine, I applied a Wireshark filter for RDP (Remote Desktop Protocol) traffic using `tcp.port == 3389`, which isolates the packets associated with RDP connections. This revealed a constant flow of traffic, including multiple connection attempts, session negotiations, or ongoing communication over the RDP protocol. By observing this traffic, I was able to analyze the behavior of RDP sessions, such as authentication attempts, the exchange of data between the client and server, and any potential issues like unauthorized access attempts or network performance concerns.
</p>
<br />
