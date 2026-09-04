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


<h2>Creating Virtual Machines</h2>

<img width="470" height="201" alt="image" src="https://github.com/user-attachments/assets/1e4f0267-5ff9-4485-84e1-b170a3303827" />

In Microsoft Azure clicked create new Resource Group

<img width="503" height="635" alt="image" src="https://github.com/user-attachments/assets/e7753256-081c-421e-84bf-e15fae7ae8d5" />

Named the Resource Group RG-Network-Activities, selected West US 2 Region and clicked review + create

<img width="606" height="254" alt="image" src="https://github.com/user-attachments/assets/184bdf42-0f4d-47f7-8c17-842779ffa21b" />

Resource Group created successfully

<img width="468" height="211" alt="image" src="https://github.com/user-attachments/assets/2d6360b2-3a19-4d0b-8ca3-436170d07187" />

Clicked create Virtual Machine

