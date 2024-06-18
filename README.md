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

- Create our Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
- Lab Cleanup (DON'T FORGET THIS)

<h2>Actions and Observations</h2>

<p>
<img width="600" alt="Screenshot 2024-06-15 at 11 22 08 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/7b2a4aa9-d866-4d3d-8408-e181083c6b43">
<img width="600" alt="Screenshot 2024-06-15 at 11 25 47 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/38db5569-8e4e-4d28-8f8d-c98f43ff6483">
<img width="600" alt="Screenshot 2024-06-15 at 11 31 19 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a49b0d58-85f1-4510-adf1-bc86f30857ee">
<img width="600" alt="Screenshot 2024-06-15 at 11 41 20 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a156e00e-d00b-49e7-b2b5-8a61068ac63b">
</p>
<p>
  
- **Create our Resources**
- Create Windows 10 Virtual Machine and Resource Group Simultaneously
- Create Linux(Ubuntu) VM in same Resource Group and Virtual Network
</p>
<br />

<p>
<img width="600" alt="Screenshot 2024-06-15 at 11 53 42 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/d62bf5d6-b5c9-49a0-a761-46088d4f9361">
<img width="600" alt="Screenshot 2024-06-15 at 11 56 28 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ef0f0367-14b5-4815-ab4c-e6469fb25dca">
<img width="600" alt="Screenshot 2024-06-15 at 11 59 13 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a0d36863-7b8f-451e-ac2e-b2b57c080811">
<img width="600" alt="Screenshot 2024-06-15 at 12 00 01 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/07a91633-518c-45c2-859e-ddbc172d7817">
<img width="600" alt="Screenshot 2024-06-15 at 12 01 20 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ab73987c-8a97-45bb-97fa-6fb7110fbb88">
<img width="600" alt="Screenshot 2024-06-15 at 12 08 15 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ef9b96d2-1418-4c3b-83ee-412ab0ea13a3">
<img width="600" alt="Screenshot 2024-06-15 at 12 03 09 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/1a0dab20-f1cb-46e4-959d-1772b17fb922">
<img width="600" alt="Screenshot 2024-06-15 at 12 03 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/34401bd4-9ed2-4b90-9a65-daf85cc683cd">
<img width="600" alt="Screenshot 2024-06-15 at 12 12 50 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/2c351ae9-d8e1-47cd-aee5-214ca4899b44">
<img width="600" alt="Screenshot 2024-06-15 at 12 12 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/76d32b41-34ba-44ce-80b2-c62b67361bd9">
<img width="600" alt="Screenshot 2024-06-15 at 12 14 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/3b270243-b9af-43c3-9fa9-0003f59dd10e">
<img width="600" alt="Screenshot 2024-06-15 at 12 15 34 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/d6023dbf-eb01-45e7-8b98-59f8f064bb4c">
<img width="600" alt="Screenshot 2024-06-15 at 12 16 16 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/f4f9b44e-92c8-47b4-af8f-7b77469d9dba">
</p>
<p>
  
- **Observe ICMP Traffic**
- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and filter for ICMP traffic only
- Retrieve the pricate IP address of the Ubuntu VM and attempt to ping a pubblic websire (such as www.google.com) and observe the traggic in WireShark
- Initiate a perpetual/non-stop ping from your Windows 1- VM to your Ubuntu VM
  1. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
  2. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
  3. Stop the ping activity
</p>
<br />

<p>
<img width="600" alt="Screenshot 2024-06-15 at 12 23 13 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/caf1681f-3196-4912-96f2-12bc4696fff4">
<img width="600" alt="Screenshot 2024-06-15 at 12 25 56 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/94630be8-77e2-48f5-8759-459a410b9357">
<img width="600" alt="Screenshot 2024-06-15 at 12 27 48 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/b3db07ed-8907-4afe-bb33-35474344eac7">

</p>
<p>
  
- **Observe SSH Traffic**
- Back in Wireshark, filter for SSH traffic only
- From your Windows 10 VM, "SSH into" your Ubuntu Virtual Machine (via its private IP address)
  1. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
  2. Exit the SSH connention by typing 'exit' and presssing [Enter]
</p>
<br />

<p>
<img width="600" alt="Screenshot 2024-06-15 at 12 38 29 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a73d2510-b8b3-4a1d-b718-4906998effa2">
</p>
<p>
  
- **Observe DHCP Traffic**
- Back in Wireshark, filter for DHCP traffic only
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig / renew)
  1. Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img width="600" alt="Screenshot 2024-06-15 at 12 41 55 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/e08d98d9-90bc-45ed-9818-55558fefdc01">
</p>
<p>
  
- **Observe DNS Traffic**
- **Observe RDP Traffic**
- **Lab Cleanup (DON'T FORGET THIS)**
</p>
<br />

