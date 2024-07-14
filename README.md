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

- Create Virtual Machines in Azure (Windows 10 and Linux)
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
- Lab Cleanup (DON'T FORGET THIS)

<h2>Actions and Observations</h2>

<p>

  - **Create our Resources**
</p>
<p>
<img width="300" alt="Screenshot 2024-07-11 at 11 02 47 AM" src="https://github.com/user-attachments/assets/466c2892-7afb-41ed-b66b-86e5e16e51d3">
</p>
<p>
  
- Log-In to Microsoft Azure by going to https://portal.azure.com
</p>
<br />


<p>
<img width="300" alt="Screenshot 2024-07-11 at 11 05 49 AM" src="https://github.com/user-attachments/assets/6ec78856-9dc5-406b-bba1-6f8801aea1be">
<img width="250" alt="Screenshot 2024-07-11 at 11 10 31 AM" src="https://github.com/user-attachments/assets/d897eef6-deb6-4f99-9da0-ac3d23ecec86">
<img width="300" alt="Screenshot 2024-07-11 at 11 13 07 AM" src="https://github.com/user-attachments/assets/bcdb18d9-58ec-46f1-a1f4-2d0526d254b8">
<img width="300" alt="Screenshot 2024-07-11 at 11 18 03 AM" src="https://github.com/user-attachments/assets/2f591390-2d1a-46f4-87fd-aee40bb9c4bb">
<img width="300" alt="Screenshot 2024-06-15 at 11 25 47 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/38db5569-8e4e-4d28-8f8d-c98f43ff6483">
  
</p>
<p>
  
- Click "Resources" icon at home page
- Select Create New Resource Group ("Tejanos")
- Return to Home page and Click "Virtual Machines" icon
- Create Windows 10 Virtual Machine inside of the created Resourse group ("VM-1")
- Notice the details of the Virtual Machine 
</p>
<br />

<p>
<img width="300" alt="Screenshot 2024-07-11 at 11 12 07 AM" src="https://github.com/user-attachments/assets/c6c9d421-502c-496c-bdec-0b8ddea74cc9">
<img width="300" alt="Screenshot 2024-07-11 at 11 23 41 AM" src="https://github.com/user-attachments/assets/c4c6dafd-0544-4f90-9c53-4dcfd4160ebf">
<img width="300" alt="Screenshot 2024-07-11 at 11 25 53 AM" src="https://github.com/user-attachments/assets/a5e989ce-c688-46d7-91a4-cfa14700d597">
<img width="300" alt="Screenshot 2024-07-11 at 11 27 22 AM" src="https://github.com/user-attachments/assets/3fcb97f8-10a2-4be2-9f49-51dba18cd4b3">
<img width="300" alt="Screenshot 2024-07-11 at 11 28 03 AM" src="https://github.com/user-attachments/assets/132d785e-8879-4ce3-83f3-6148212cfdb2">
<img width="300" alt="Screenshot 2024-07-11 at 11 29 18 AM" src="https://github.com/user-attachments/assets/3b80699d-2a5e-4f02-bad7-abec48da7318">
<img width="300" alt="Screenshot 2024-06-15 at 11 41 20 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a156e00e-d00b-49e7-b2b5-8a61068ac63b">
</p>
<p>

- Go to home page, Click "Virtual Machine"
- Create Linux(Ubuntu) Virtual Machine ("VM2") in same Resource Group as VM-1 ("Tejanos")
- Under "Administrator Account" and "Authentication Type" click "Password"
- Create a username and password for this Linux VM
- Go to "Networking" and make sure this VM is on the same Virtual Network as "VM-1"
- Go on to "Review + Create" Virtual Machine
- Go to Virtual Machines and observe both Virtual Machines are in same Resource Group
</p>
<br />

<p>
<img width="300" alt="Screenshot 2024-07-11 at 11 37 21 AM" src="https://github.com/user-attachments/assets/f8005dde-dab7-4969-8bda-6f029f98229b">
<img width="300" alt="Screenshot 2024-07-11 at 11 38 02 AM" src="https://github.com/user-attachments/assets/52850906-6feb-4d8f-8dc3-4ab386fb1a1f">
<img width="300" alt="Screenshot 2024-07-11 at 11 39 05 AM" src="https://github.com/user-attachments/assets/23deb618-bbb2-4cf8-96b6-d0feb222da00">
<img width="300" alt="Screenshot 2024-07-11 at 11 39 24 AM" src="https://github.com/user-attachments/assets/ad04e953-acf5-4bb4-b689-6773b8d91365">
<img width="300" alt="Screenshot 2024-07-11 at 11 39 42 AM" src="https://github.com/user-attachments/assets/3adfda55-c352-4dfc-bf9f-610fbacddbfc">
<img width="300" alt="Screenshot 2024-07-11 at 11 39 49 AM" src="https://github.com/user-attachments/assets/273d8503-6258-4752-8c48-14c286438d45">
<img width="300" alt="Screenshot 2024-07-11 at 11 40 06 AM" src="https://github.com/user-attachments/assets/4ea5544d-49a2-4971-862e-1f0347b2c7ad">
<img width="300" alt="Screenshot 2024-07-11 at 11 42 06 AM" src="https://github.com/user-attachments/assets/c185c9e3-83f1-4faf-9d94-c799bf6edf8a">
<img width="300" alt="Screenshot 2024-07-11 at 11 45 13 AM" src="https://github.com/user-attachments/assets/d0883579-1f45-4c7b-bfd9-1d9f44341cf5">

</p>
<p>
  
- **Access Remote Desktop**
- Open "Microsoft Remote Desktop" to access "VM-1" 
- Click "Add PC"
- Go to Virtual Machines and click VM-1 to access details. Copy the IP address of the "VM-1"
- Click Connect
- Log-in with username and password created for VM-1, Click "Continue"
- You should observe the Log In Screen, then the Desktop
- Go to a web browser to access www.wireshark.org to prepare for next step 
</p>
<br />

<p>

<img width="300" alt="Screenshot 2024-07-11 at 11 45 23 AM" src="https://github.com/user-attachments/assets/aa374cde-4c39-44ec-876e-20df61f7a4b6">
<img width="300" alt="Screenshot 2024-07-11 at 11 45 39 AM" src="https://github.com/user-attachments/assets/d0d79365-b907-4ebf-8b8c-1f3c983c5149">
<img width="300" alt="Screenshot 2024-07-11 at 11 54 59 AM" src="https://github.com/user-attachments/assets/a85befb6-98fd-4d99-9612-233a8e553613">
<img width="300" alt="Screenshot 2024-07-11 at 11 55 17 AM" src="https://github.com/user-attachments/assets/7edafb66-2ccd-41e9-96b5-0cc32e059023">
<img width="300" alt="Screenshot 2024-07-11 at 12 00 26 PM" src="https://github.com/user-attachments/assets/f8c3dab0-1589-4865-b44d-6710723c80c7">
<img width="300" alt="Screenshot 2024-07-11 at 12 01 44 PM" src="https://github.com/user-attachments/assets/8d620882-958a-49b5-8be3-76206da0352a">
</p>
<p>
  
- **Install Wireshark**
- Click Windows x64 Installer
- Open installer file
- Follow prompts in order to complete installation
- Open Wireshark to begin Testing

</p>
<br />

<p>
<img width="250" alt="Screenshot 2024-06-15 at 11 56 28 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ef0f0367-14b5-4815-ab4c-e6469fb25dca">
<img width="250" alt="Screenshot 2024-06-15 at 11 59 13 AM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a0d36863-7b8f-451e-ac2e-b2b57c080811">
<img width="250" alt="Screenshot 2024-06-15 at 12 00 01 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/07a91633-518c-45c2-859e-ddbc172d7817">
<img width="250" alt="Screenshot 2024-06-15 at 12 01 20 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ab73987c-8a97-45bb-97fa-6fb7110fbb88">
<img width="250" alt="Screenshot 2024-06-15 at 12 08 15 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/ef9b96d2-1418-4c3b-83ee-412ab0ea13a3">
<img width="250" alt="Screenshot 2024-06-15 at 12 03 09 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/1a0dab20-f1cb-46e4-959d-1772b17fb922">
</p>
<p>
  
- **Observe ICMP Traffic**
- Click Blue Fin in top left Corner to initiate observation of ethernet traffic
- Within search bar of Wireshark filter for ICMP traffic only
- Go to Microsoft Azure homepage and access Virtual Machines page. Click on VM2 to access details 
- Retrieve the private IP address of the Ubuntu VM (in this case = 10.0.0.5.)
- Open Powershell to attempt to ping Ubuntu Server ("VM2"). type "ping 10.0.0.5" (or whatever the private address is you are working with)
- Observe Traffic in Wireshark

</p>
<br />

<p>

<img width="250" alt="Screenshot 2024-06-15 at 12 03 09 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/1a0dab20-f1cb-46e4-959d-1772b17fb922">
<img width="250" alt="Screenshot 2024-06-15 at 12 03 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/34401bd4-9ed2-4b90-9a65-daf85cc683cd">
<img width="250" alt="Screenshot 2024-06-15 at 12 12 50 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/2c351ae9-d8e1-47cd-aee5-214ca4899b44">
<img width="250" alt="Screenshot 2024-06-15 at 12 12 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/76d32b41-34ba-44ce-80b2-c62b67361bd9">
<img width="250" alt="Screenshot 2024-06-15 at 12 14 22 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/3b270243-b9af-43c3-9fa9-0003f59dd10e">
<img width="250" alt="Screenshot 2024-06-15 at 12 15 34 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/d6023dbf-eb01-45e7-8b98-59f8f064bb4c">
<img width="250" alt="Screenshot 2024-06-15 at 12 16 16 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/f4f9b44e-92c8-47b4-af8f-7b77469d9dba">
</p>
<p>
  
- **Observe ICMP Traffic cont.**
- Initiate a perpetual/non-stop ping ("ping 10.0.0.5 -t") from your Windows 10 - "VM-1" to your Ubuntu VM - "VM2"
  1. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
  2. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
  3. Stop the ping activity
</p>
<br />

<p>
<img width="300" alt="Screenshot 2024-06-15 at 12 23 13 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/caf1681f-3196-4912-96f2-12bc4696fff4">
<img width="300" alt="Screenshot 2024-06-15 at 12 25 56 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/94630be8-77e2-48f5-8759-459a410b9357">
<img width="300" alt="Screenshot 2024-06-15 at 12 27 48 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/b3db07ed-8907-4afe-bb33-35474344eac7">

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
<img width="300" alt="Screenshot 2024-06-15 at 12 38 29 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/a73d2510-b8b3-4a1d-b718-4906998effa2">
</p>
<p>
  
- **Observe DHCP Traffic**
- Back in Wireshark, filter for DHCP traffic only
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig / renew)
  1. Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img width="300" alt="Screenshot 2024-06-15 at 12 41 55 PM" src="https://github.com/calebdagreat/azure-network-protocols/assets/171304036/e08d98d9-90bc-45ed-9818-55558fefdc01">
</p>
<p>
  
- **Observe DNS Traffic**
- **Observe RDP Traffic**
- **Lab Cleanup (DON'T FORGET THIS)**
</p>
<br />

