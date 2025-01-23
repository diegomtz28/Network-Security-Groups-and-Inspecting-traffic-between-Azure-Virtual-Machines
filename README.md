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
