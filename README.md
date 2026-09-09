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

<img width="394" height="257" alt="image" src="https://github.com/user-attachments/assets/658ff75c-1143-4191-b434-b39115d6193a" />

Clicked create Azure virtual machine

<img width="526" height="537" alt="image" src="https://github.com/user-attachments/assets/0e9a2963-451c-42f3-ae68-154d71d8ddc7" />

Selected RG-Network-Activities Resource group, named the virtual machine windows-vm and selected East US 2 reigion

<img width="521" height="423" alt="image" src="https://github.com/user-attachments/assets/b72706f2-89df-4132-9da5-7aeb72d83e81" />

For the image selected Windows 10 Pro, version 22H2 and selected Standard size

<img width="525" height="635" alt="image" src="https://github.com/user-attachments/assets/5416ea52-6933-4b63-8f96-998bcc2aab02" />

Username: labuser Password: Cyberlab123! and then clicked next

<img width="528" height="626" alt="image" src="https://github.com/user-attachments/assets/6d8b4ad9-1bdc-4041-a3cd-a783790da44d" />

Clicked on create new virtual network and named it Lab2-Vnet and then clicked review + create to create the Windows virtual machine and the virtual network.

<img width="462" height="248" alt="image" src="https://github.com/user-attachments/assets/4a3a1665-9606-4dd9-b4da-a58846edd693" />

To create another virtual machine clicked on create new Azure virtual machine

<img width="538" height="535" alt="image" src="https://github.com/user-attachments/assets/0cabc3e1-7c6c-4e72-bc33-0e7bf3a6e093" />

Selected RG-Network-Activities Resource group and East US 2 region. Named the virtual machine linux-vm

<img width="612" height="437" alt="image" src="https://github.com/user-attachments/assets/4e3fc219-cccc-4f60-9e57-8dc316fe5e15" />

For the image selected Ubuntu Server 22.04 LTS and chose Standard size

<img width="514" height="218" alt="image" src="https://github.com/user-attachments/assets/d2b64379-b3ed-45ab-a3ae-8e006ebe6d3c" />

Username: labuser Password: Cyberlab123! and then clicked next

<img width="591" height="630" alt="image" src="https://github.com/user-attachments/assets/14b33971-4db6-4a4b-a939-397bb6e51296" />

Selected the virtual network Lab2-Vnet that was created and clicked review + create to create the linux virtual machine

<img width="777" height="301" alt="image" src="https://github.com/user-attachments/assets/24cde7d6-3b33-4714-92d9-5476b26f6d78" />

Both Windows virtual machine and linux virtual machine created successfully

<h2>Observing ICMP traffic & configuring Firewall/Network Security Group</h2>

<img width="605" height="353" alt="image" src="https://github.com/user-attachments/assets/dc5fd9e4-f3cb-4fa6-af70-e66e4e81014b" />

In Azure clicked on windows-vm Virtual machine and copied windows-vm Public IP address to connect to the virtual machine using Remote Desktop Connection

<img width="340" height="59" alt="image" src="https://github.com/user-attachments/assets/404a8b09-1a15-40f6-a8e7-2d3b757cd187" />

Clicked start menu and searched for Remote Desktop Connection

<img width="405" height="250" alt="image" src="https://github.com/user-attachments/assets/54be22e4-7cf3-4f9c-8be7-bc8577dc414e" />

Pasted windows-vm Public IP address in Remote Desktop Connection and clicked connect

---------image-----

Typed the username and password used to create the virtual machine (username: labuser  password: Cyberlab123!) and then clicked OK to connect

<img width="817" height="412" alt="image" src="https://github.com/user-attachments/assets/0edc2efe-3b26-47f8-956b-bbf72e668ca7" />

Once logged in, downloaded Wireshark in Microsoft Edge to see network traffic happening

<img width="733" height="416" alt="image" src="https://github.com/user-attachments/assets/53025819-5cb5-4ed8-95e1-b3e478f68175" />

Once downloaded, opened the file to open Wireshark Setup and clicked next

<img width="737" height="415" alt="image" src="https://github.com/user-attachments/assets/ec42de33-ba3a-43f1-a611-171efad0c379" />

Clicked next

<img width="737" height="413" alt="image" src="https://github.com/user-attachments/assets/6d5b162e-35a9-43ac-b6e6-a657ddf60a6c" />

Clicked next

<img width="735" height="415" alt="image" src="https://github.com/user-attachments/assets/3afb0dbd-1eae-4470-b290-ff2cfd3f6df8" />

Clicked install

<img width="513" height="227" alt="image" src="https://github.com/user-attachments/assets/c8faaba3-1a79-4104-b5a9-980084b6f0ec" />

When finished installing, opened Wireshark by clicking start menu and searched for Wireshark
