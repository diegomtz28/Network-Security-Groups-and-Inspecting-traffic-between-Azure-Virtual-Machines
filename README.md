<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

- Configure Azure Virtual Network and Virtual Machines
- Configure and Apply Network Security Groups (NSGs)
- Inspect Network Traffic Using Wireshark
- Verify and Monitor Azure Network Activity

<h2>Actions and Observations</h2>

<h3>Configure Azure Virtual Network and Virtual Machines</h3>


__Step to Demonstrate:__ 
1. __Create a Virtual Network(Vnet):__
  - Log in to the Azure portal and create a new Vnet with a defined address space (10.0.0.0/16)
  - Create subnets 
2. __Deploy Virtual Machines(VMs):__
   - Create two VMs in the same resource group, assigning each to one of the subnets in your VNET
   - Ensure each VM is configured with a private IP and enable the public IP required for Remote Desktop or SSH
3. __Enable Connectivity:__
   - Verify the VMs can ping each other using their private IP addresses by connecting to one VM using Remote Desktop or SSH and running basic ping commands
   - Test if the VMs can communicate without additional configurations
4. __Document Results:__
   - Highlight that the VMs are in the same VNet but separate subnets, showcasing basic connectivity

     **A screenshot of the "create a virtual network" page with the address soae=ce and subnet details, highlighting the configuration fields.**

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Configure and Apply Network Security Groups (NSGs)</h3>

__Step to Demonstrate:__ 
   1. __Create a NSG:__
      - Navigate to "Network Security Groups" in Azure, and create an NSG for each VM.
      - Assign the NSG to the subnet or the individual VM's network interface
   2. __Define Inbound and Outbound Rules:__
      - Allow SSH and RDP for specific IP ranges
      - Block all other traffic as the default rule.
   3. __Test NSG Rules:__
      - Attempt to connect to the VM using Remote Desktop or SSH from an allowed IP and confirm success
      - Attempt the same connection from a blocked IP range and confirm failure
   4. __Test Printing:__
      - Send a test print job to ensure the user can print successfully, If unsuccessful, escalate to the network or hardware team
  5. __Document Rule Configuration:__
     - Include screenshots of the NSG settings and describe how they protect the environment by controlling inbound and outbound traffic.
    
       **Nsg creation. Inbound and outbound rules, COnnection testwith nsg rules, nsg flow logs**


<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Inspect Network Traffic Using Wireshark</h3>

__Steps to Demonstrate:__
1. __Install and Configure Wireshark:__
   - Install Wireshark on one of the VMs or your local machine connected to the Azure Environment
   - Select the appropriate network adapter to monitor traffic
2. __Caoture Traffic:__
   - Start a packet capture session on the VM while initiating communication with the second VM(Ping or SSH Traffic)
   - Filter packets for specific protocols (ICMP for ping, TCP for SSH)
3. __Analyze Captured Data:__
   - Highlight specific packets, such as DNS queries or TCP handshake processes, to demonstrate understanding of protocol-level traffic
   - Document key observations, like latency, handshake duration, or protocol use
4. __Document Findings:__
   - Include screenshots of the Wireshark interface, highlighting specific packaet captures and their interpretation
  
     **Wireshark setup, captured traffic, filtered traffic, packet analysyis**
   


<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Verify and Monitor Azure Network Activity</h3>

__Steps to Demonstrate:__
1. __Enable Network Watcher:__
   - Turn on Azure Network Watcher for the region where your VMs are deployed
   - Use Network Watcher tools like "COnnection Monitor" to verify connectivity between VMs
2. __Run Network Diagnostic Tools:__
   - Use tools like nslookup, tracert, and ping within the VM to test connectivity to other VMs or external endpoints
   - Verify DNS resolution and routing paths using these tools
3. __Set Up Traffic Flow Logs:__
   - Enable NSG flow logs to monitor allowed denied traffic through the NSG
   - Use Azure Storage or Log Analytics to analyze flow logs and identify unusual traffic patterns
4. __Document Results:__
   - Share insight on connectivity and log analysis, emphasizing how to monitor traffic for security or performance concerns
   **Azure network watcher, diagnosrtic tools(comand line), nsg flow logs**
