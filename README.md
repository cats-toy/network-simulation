# Network-simulation
<img src = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSo9czzc_9olMMpCxwiG36cqAi9kywi-gduJCV9B1X3mYAZx90-BXO8cpVywRNV5x6BbkU&usqp=CAU.png" width = 400 height = 300>
<h1>Table of contents</h1>

- Tools used
- EVE-NG
- Cisco Packet Tracer
- Outcomes

 <h1>Tools Used</h1>

  1. VMware workstation
  2. EVE-NG
 
<h1>EVE-NG</h1>
<p>EVE-NG is a powerful network emulation and virtualization software. It's mainly used to create network topologies on server for learning and testing purposes</p>
<p>EVE-NG is mainly used for:<br>
- Proof of concept <br>
- Network Automation<br>
- Troubleshooting<br>
- Experimentation</p>
<p>In this project, I'll use EVE-NG to recreate some network topologies used in real life networks. I'll be applying various network concepts such as WAN/SD-WAN to connect multiple sites to each other, subnetting and VLANs to separate network interfaces and routing tables.</p>
<h1>Installation</h1>
<p>The ISO for the EVE-NG community version can be installed here, <a href="https://www.eve-ng.net/index.php/download/#DL-LIN">EVE-NG Downloads</a></p>
<p>EVE-NG is compatible with VMware version 16 and later. The VMware can be installed here, <a href="https://support.broadcom.com/">VMware Broadcom.</a> For VMware, you'll need to register for an account with Broadcom. In software, click on VMware Cloud Foundation, My Downloads and then install VMware workstation version 16.0.0. </p>
<p>After installation, create a new VM(virtual machine) with VMware and follow the <a href="https://www.eve-ng.net/images/EVE-COOK-BOOK-1.0.pdf">EVE-NG cookbook</a> to properly install the EVE-NG community ISO.</p> 
<p>To enable Virtualized Intel VT-x/EPT, HyperV needs to be turned off if you're using Windows. Search msinfo32 to bring up the System Information panel and find Virtualization-based Security, if its running then you're HyperV is on. Next, search "Turn Windows Features on and off" and make sure HyperV is not ticked. Open up command prompt on admin and run these commands,</p> 
 
 ```
 bcdedit /enum {current}
 bcdedit /set hypervisorlaunchtype off
 ```
<p>Run bcdedit /enum {current} again to check that hypervisorlaunchtype is off.</p>
<p>Finally we need to ensure Memory Integrity is off, navigate to Windows Security, Device Security and in Core Isolation Details untick Memory Integrity. Reboot your computer and check msinfo32 again to confirm that Virtualization-based Security is off. </p>
<p>After installing and configuring your EVE-NG community VM, we can login to the EVE-NG CLI by typing the IP address of the EVE-NG VM into a browser.</p>

<h1>Constructing network topologies</h1>
<h2>Basic BGP routing</h2>
<p>Border Gateway Protocol(BGP) is a gateway protocol that is used to transfer or exchange routing and reachability information amoing autonomous systems. In this lab, I set up two routers and two virtual computer nodes. I used BGP to connect the two routers to each other to allow contact between the nodes in the different subnets. I was able to ping VPC4 from VPC3. The nodes use the Cisco CLI to run commands. I assigned IP addresses to each router's interface, e0/0 facing the internet and e0/1 facing their respective VPC. I set the IP addresses and default gateways for the VPCs as well.</p>
<img src="https://imgur.com/mkTCKGU.png" width = 400 height = 200>

<h2>BGP routing, multiple subnets</h2>
