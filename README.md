<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Step 1 (Observe ICMP Traffic)
- Step 2 (Configuring a Firewall [Network Security Group])
- Step 3 (Observe SSH Traffic)
- Step 4 (Observe DHCP Traffic)
- Step 5 (Observe DNS Traffic)
- Step 6 (Observe RDP Traffic)

<h2>Actions and Observations</h2>

![image](https://github.com/user-attachments/assets/39272951-e508-40c6-925e-6984dadbace7)

- If using Mac, install Microsoft Remote Desktop,
Use Remote Desktop to connect to your Windows 10 Virtual Machine,
Within your Windows 10 Virtual Machine, Install Wireshark,
Open Wireshark and start packet capture,
Within Wireshark, filter for ICMP traffic only,
Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM,
Observe ping requests and replies within WireShark,
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website and observe the traffic in WireShark.


![image](https://github.com/user-attachments/assets/c801618e-e83b-4ba1-9a2e-ec0283bd6136)


![image](https://github.com/user-attachments/assets/4c5e87be-a1bc-4ab6-957e-c1433b0c0ab5)


- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM,
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic,
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity,
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is,
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working),
Stop the ping activity.


![image](https://github.com/user-attachments/assets/82460ff8-b518-4455-87db-8f09c76c2c0f)


- Log back into the windows-vm,
Back in Wireshark, start a packet capture up,
Filter for SSH traffic only,
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address),
Open PowerShell, and type: ssh labuser@<private IP address>,
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark,
Exit the SSH connection by typing ‘exit’ and pressing [Enter].

![image](https://github.com/user-attachments/assets/7620559b-ea86-4787-bd74-edcf7cbd0a07)



- Back in Wireshark, filter for DHCP traffic only,
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line,
Open PowerShell as admin and run: ipconfig /renew,
Observe the DHCP traffic appearing in WireShark.


![image](https://github.com/user-attachments/assets/36e44fa8-49ab-44cd-8edb-c84b47ddedd2)


- Back in Wireshark, filter for DNS traffic only,
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are,
Observe the DNS traffic being show in WireShark.


![image](https://github.com/user-attachments/assets/387e615b-11d4-4827-8219-9b5c69619efc)


- Back in Wireshark, filter for RDP traffic only (tcp.port == 3389),
Observe the immediate non-stop spam of traffic.
