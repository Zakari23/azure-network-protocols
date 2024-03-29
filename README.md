# Azure-Network-Protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark. <br />


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

- Create a resource group along with two virtual machines
- Observed TCMP, SSH, DHCP, and RDP traffic 


<h2>Actions and Observations</h2>

<p>
Step .1 Create a resource group, within that resource group create one virtual machine running on Windows and another running on Ubuntu
<p></p>
  <img width="1420" alt="Screenshot 2024-03-16 at 11 14 08 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/c1cf2b7c-d29d-4937-b036-ecf54e1aa01e">
<img width="1410" alt="Screenshot 2024-03-16 at 11 18 46 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/9e0d3986-f36b-4c8b-b122-bb1c98257fe2">
<img width="1419" alt="Screenshot 2024-03-16 at 11 21 30 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/d2d06f03-5604-45bb-b2f0-873e56f4baf7">

</p>
<p>
Step 2. Install Wireshark on your Windows (VM1)
</p>
<br />
<img width="1283" alt="Screenshot 2024-03-16 at 11 42 01 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/e585b95e-efae-4fc0-a2e4-18942ad82bd3">
<img width="515" alt="Screenshot 2024-03-16 at 11 45 10 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/52910264-3045-4ce7-bc78-a591033cf924">
<p></p>

<p></p>
Step 3. After I installed Wireshark on my Windows 10 virtual machine (VM1), I opened the app and set it to only show ICMP traffic. Then, I used PowerShell to ping the private IP address of my Ubuntu virtual machine (VM2) from within VM1. As a result, I could see both the ping requests and replies in Wireshark. 
<p>
</p>
<img width="319" alt="Screenshot 2024-03-16 at 11 56 31 PM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/f64492e2-cf87-4969-9979-84f19e506092"> 
<img width="1142" alt="Screenshot 2024-03-17 at 12 35 22 AM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/3853a142-57df-4af8-99a8-ae079c6ba048">

</p>
<p>
Step 4. After that, I used Wireshark to only show SSH (Secure Shell) traffic. At the same time, I went to the PowerShell terminal and started an SSH connection to VM2. While connected, I ran commands, which made SSH packets show up in Wireshark. When I finished, I typed "exit" to end the SSH session.
<p></p>
<img width="1154" alt="Screenshot 2024-03-17 at 2 02 42 AM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/0fbbb5da-8833-429d-a24b-28c0ed052916">

</p>
<br />
Step 5. In Wireshark, I used a filter udp.port == 53 to show DNS (Domain Name System) traffic. Then, I ran the "nslookup" command for www.google.com This command asks our DNS server for the IP addresses linked to "google.com" domain names.

<p></p>
<img width="1327" alt="Screenshot 2024-03-17 at 3 03 48 AM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/4d9c9104-de23-44b2-aa4e-366585b85ddf">
<p>
Step 6 Finally, I used a filter in Wireshark to show RDP (Remote Desktop Protocol) traffic, focusing on the TCP port number (tcp.port==3389). RDP is the protocol for connecting to other computers remotely, giving full control over the Graphical User Interface (GUI). During the observation, there was a steady flow of RDP traffic.

</p>
<img width="1163" alt="Screenshot 2024-03-17 at 2 42 02 AM" src="https://github.com/Zakari23/azure-network-protocols/assets/158666482/22fd6f65-dbe8-4ab8-a5e1-1704fee55ab2">
