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

<h2>Actions and Observations</h2>

You will need 2 Virtual Machines: a Windows 10 VM and a Linux (Ubuntu) VM. Allow your Windows VM to create a new Virtual Network(Vnet) and Subnet. Your Linux VM will be on the same resource group AND virtual network as your other VM.

<img width="1348" height="167" alt="image" src="https://github.com/user-attachments/assets/955b9592-f694-4de3-a6dc-00b33942fffd" />


<img width="966" height="369" alt="image" src="https://github.com/user-attachments/assets/f89e7e3a-ad9e-443b-9aae-3d99ad7563cb" />

Within Windows 10 VM, install Wireshark. Open Wireshark and packet capture. Filter for ICMP traffic.

<img width="932" height="191" alt="image" src="https://github.com/user-attachments/assets/81c19af1-577b-42ae-b5ae-507713acc735" />

Copy the private IP Address of the Ubuntu VM and ping it from the Windows 10 VM.

<img width="792" height="628" alt="image" src="https://github.com/user-attachments/assets/52f11a43-cac9-4459-a364-08dad8cccbf5" />

Attempt to ping a public website like www.google.com and observe the traffic in WireShark.
<img width="775" height="574" alt="image" src="https://github.com/user-attachments/assets/f733bf71-7007-4c9a-a1d9-321bff36e920" />

<h2>Firewall Configuration</h2>

Now we're going to configure a firewall in our Network Security Group. First, we initiate a non-stop ping from our Windows 10 VM to our Ubuntu VM.

<img width="788" height="641" alt="image" src="https://github.com/user-attachments/assets/a95feb88-6fbf-4973-a446-459d673b789f" />

Open the Network Security Group your Ubuntu VM is using and disable incoming ICMP traffic.

<img width="871" height="665" alt="image" src="https://github.com/user-attachments/assets/fb49bd96-9865-4b6c-b484-c341b005d473" />

<img width="436" height="763" alt="image" src="https://github.com/user-attachments/assets/021faa86-8e0c-4e2c-9a3d-39c7568d0f70" />

Observe the ping requests within WireShark and command line ping activity in Powershell within the Windows 10 VM.

<img width="826" height="677" alt="image" src="https://github.com/user-attachments/assets/c1c3ee6c-9f24-480d-8f49-77bfa6f13e8b" />

