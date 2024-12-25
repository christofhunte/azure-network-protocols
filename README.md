<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this project, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/XHYAKR3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First step was to create a Resource Group in the Azure Portal.
</p>
<br />

<p>
<img src="https://i.imgur.com/Ke6a9Df.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to create a Virtual Network (Vnet) and Subnet in the Azure Portal.
</p>
<br />

<p>
<img src="https://i.imgur.com/CxuBiPL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rfwypfV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ufUOve6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to create a Virtual Machine for Windows 10 within the Resource Group, Virtual Network and Subnet previously created.
</p>
<br />

<p>
<img src="https://i.imgur.com/eZZW0FL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/lsGCuVp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/unFjs5l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to create a Virtual Machine for Linux (Ubuntu) within the Resource Group, Virtual Network and Subnet previously created.
</p>
<br />

<p>
<img src="https://i.imgur.com/4HPWRao.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BPekAJ7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2hEKpzH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ryfgquj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to take the Public IP Address of the Windows Virtual MAchine and login to it through Microsoft Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/k2nsgf2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NjAopoM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to install Wireshark within the Windows Virtual Machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/xoYdOsn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/tzPoyox.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to open Wireshark within the Windows Virtual Machine and start a packet capture.
</p>
<br />

<p>
<img src="https://i.imgur.com/o5fS82K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cEH8RdY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to filter for ICMP traffic only within Wireshark. Then I opened up Powershell, retrieved the private IP address of the Ubuntu VM (linux-vm) and attempted to ping it from within the Windows 10 VM. I then observed the ping requests and replies within Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/Z9uXw4Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next I initiates a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM for the purpose testing a Firewall (Network Security Group) configuration within the Azure Portal.
</p>
<br />

<p>
<img src="https://i.imgur.com/5CNqRJg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8Rs7VMk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/UQ547xH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next I opened the Network Security Group the Ubuntu VM is using and disabled incoming (inbound) ICMP traffic with a higher priority ranking.
</p>
<br />

<p>
<img src="https://i.imgur.com/bbdkLi4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/PIHGAoC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/bzG8nYL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next I observed the ICMP traffic in WireShark and the command line Ping activity which stopped because of the Firewall. I then deleted the Firewall which re-enabled ICMP traffic for the Network Secuirty Group thr Ubuntu Virtual Machine is. I observed the traffic again in Wireshark and saw that it started back.
</p>
<br />

<p>
<img src="https://i.imgur.com/XfaMGQd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8LQ61lh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/lRbhyRq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step was to start a new packet capture in Wireshark, and filter for SSH traffic only. I started testing commands (username, pwd, etc) into the linux SSH connection to observe SSH traffic spam in WireShark.

</p>
<br />


