<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop
- Microsoft PowerShell
- Various Network Protocols (SSH, RDH, DNS, DHCP, ICMP)
- Wireshark

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource
- Capture and Study ICMP activity
- Capture and Study SSH  activity
- Capture and Study DHCP activity
- Capture and Study DNS activity
- Capture and Study RDP activity


<h2>Processes and Observations</h2>


<p>
<img src="https://i.imgur.com/3ujdSId.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, create a resource group in Microsoft Azure. We'll be using two Virtual Machines (VMs) one running Windows 10 and another running Linux (Ubuntu). Make sure they are in the same Virtual Network (Vnet).
</p>
<br />

<p>
<img src="https://i.imgur.com/KCzYEU8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  <p>
<img src="https://i.imgur.com/gn24LIo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/mXksz9v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Let’s get started! Use Remote Desktop to connect to the Windows 10 VM. Once connected, install Wireshark—this powerful tool will help you analyze network traffic with precision. After installation, launch Wireshark and apply a filter for ICMP traffic to streamline your observations.
Next, locate the private IP address of the Ubuntu VM within Azure, and from the Windows 10 VM, send a ping using either the command line or PowerShell. Watch the ping requests and replies in real-time, gaining insight into their communication.
Now, for the next step: initiate a continuous ping from the Windows 10 VM to the Ubuntu VM. Navigate to the Network Security Group associated with the Ubuntu VM, and temporarily block inbound ICMP traffic. Return to Wireshark and observe how the traffic patterns change. When you’ve finished analyzing, re-enable ICMP traffic to restore full functionality.
This hands-on approach ensures a deeper understanding of how network configurations and security settings impact communication.

</p>
<br />

<p>
<img src="https://i.imgur.com/vZ1Pwqw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, let’s return to Wireshark and refine our focus by filtering for SSH traffic. From the Windows 10 VM, establish an SSH connection to the Ubuntu VM using its private IP address. Simply run the command ssh username@ip.address in your terminal, replacing username and ip.address with the appropriate details.
After entering the password, you’ll know the connection was successful when your terminal’s prompt changes—often with a color shift to indicate you’re now logged into the Ubuntu VM. Explore as needed, and when you’re ready to wrap up, just type exit to gracefully close the session.

</p>
<br />

<p>
<img src="https://i.imgur.com/V6hfBqR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Let’s head back into Wireshark and narrow our focus to DHCP traffic. From the Windows 10 VM, attempt to issue it a new IP address by running the command ipconfig /renew. Watch as the DHCP traffic springs to life, showing the process in action.
</p>
<br />

<p>
<img src="https://i.imgur.com/8JI3uoe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, shift the Wireshark filter to DNS traffic. Using the Windows 10 VM, run the command nslookup google.com to resolve Google’s IP address. Observe how the DNS queries and responses are captured in real-time—it’s like seeing the internet’s phonebook in action!
</p>
<br />

<p>
<img src="https://i.imgur.com/nkyjinO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, set your filter to capture RDP traffic, or use tcp.port==3389 for a more specific view. Notice the constant stream of data: the RDP protocol continuously transmits information to provide a live feed between the two systems. This steady flow is why you’ll see non-stop traffic—it’s the lifeblood of remote desktop connectivity.
</p>
<br />
