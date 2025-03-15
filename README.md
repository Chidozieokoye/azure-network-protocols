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

1 <h2>Create a Virtual Network and Subnet</h2>









<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

2 <h2>Create Windows 10 and Linux (Ubuntu)  Virtual Machines and join them to the same V-net</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

3 <h2>Login to Windows 10 (VM) and filter ICMP Traffic using Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

4 <h2>Inside Windows 10 (VM), ping the Ubuntu (VM) private IP address and observe ping requests and replies within Wireshark.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

5 <h2>Inside Windows 10 (VM), use PowerShell and ping a public website (Eg:www.google.com) and observe the traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

6 <h2>Configure a Firewall [Network Security Group] by disabling and enabling ICMP traffic and observe ICMP traffic activities in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

7 <h2>From Windows 10 VM, “SSH into” Ubuntu Virtual Machine (via its private IP address) and observe SSH Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

8 <h2>From Windows 10 VM, attempt to issue your VM a new IP address with PowerShell and Observe DHCP Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

9 <h2>From Windows 10 VM, inside PowerShell, use nslookup to see the IP addresses of google.com and disney.com, and observe DNS Traffic in Wireshark</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

10 <h2>From Windows 10 VM, Inside Wireshark, filter for RDP traffic (tcp.port == 3389) and observe the immediate non-stop spam of traffic.</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
