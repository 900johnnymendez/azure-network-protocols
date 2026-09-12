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

<img width="424" height="248" alt="image" src="https://github.com/user-attachments/assets/e8f50cc6-221b-47b5-842f-445933f7d7b7" />

Once opened, clicked on Ethernet

<img width="372" height="214" alt="image" src="https://github.com/user-attachments/assets/f543e219-0522-45b1-a224-37e989b45306" />

Clicked on the blue shark fin icon

<img width="773" height="377" alt="image" src="https://github.com/user-attachments/assets/61e1d20d-b0fd-4e74-8e48-6b9235263985" />

All the network traffic that happens in the background will show

<img width="530" height="376" alt="image" src="https://github.com/user-attachments/assets/7800d325-9d39-4a74-853d-cb669bac6c95" />

Where it says No. it shows the number of packets being sent to and from the virtual machine

<img width="453" height="188" alt="image" src="https://github.com/user-attachments/assets/b55afbd4-8570-4b2e-9406-994b1fec2ee5" />

Filtered for icmp traffic by typing icmp in the search and pressed enter

<img width="232" height="245" alt="image" src="https://github.com/user-attachments/assets/bc10768b-680c-4ff8-be5f-3c08d9b844bc" />

Opened Powershell by clicking start and searching for Powershell

<img width="585" height="249" alt="image" src="https://github.com/user-attachments/assets/445764ee-b8c8-4155-b84f-c439525b74ac" />

Copied the linux vm's Private IP address 10.0.0.5

<img width="1179" height="652" alt="image" src="https://github.com/user-attachments/assets/07055db3-106c-4be9-8d8b-2df0500564e8" />

Back in Powershell typed ping 10.0.0.5 to ping to the linux-vm from the windows-vm and Powershell shows 4 events from the linux-vm and Wireshark shows 8 events. Powershell shows the 4 replies from the linux-vm but Wireshark shows 8 events because it captured both the requests from the windows-vm and the replies from the linux-vm.

<img width="978" height="270" alt="image" src="https://github.com/user-attachments/assets/81c9dfa3-5452-4caf-a7ac-918d28613e62" />

The ping request shows its from the private IP address of the windows-vm (10.0.0.4) to the destination which is the linux-vm that has a private IP address of 10.0.0.5

<img width="757" height="664" alt="image" src="https://github.com/user-attachments/assets/a3b7c7c6-399a-41cc-8680-675a4a068c67" />

Clicked on one of the network traffic that was captured in Wireshark and clicked on Ethernet ||. There it shows the source and destination's Mac address. The source Mac address is the windows-vm mac address and the destination Mac address is the linux-vm's mac address.

<img width="504" height="483" alt="image" src="https://github.com/user-attachments/assets/a5d76a6b-f1bf-46b3-a3e1-e14c208c8e42" />

In Powershell typed ipconfig /all

<img width="1165" height="639" alt="image" src="https://github.com/user-attachments/assets/38d26ded-46db-4d8c-b35a-c529b7c3d9ba" />

The physical address shown in Powershell is the mac address for the windows-vm currently in use, and it shows in the source mac address in Wireshark because the ping came from the windows-vm.

<img width="1169" height="661" alt="image" src="https://github.com/user-attachments/assets/4b7498d1-1cc0-4875-a6fb-709277051715" />

The windows-vm Private IP address 10.0.0.4 shown in Powershell is shown in Wireshark under Internet Protocol in the source address.

<img width="757" height="666" alt="image" src="https://github.com/user-attachments/assets/bd5aef83-b990-47e8-a88a-d4a563a492bc" />

The destination address 10.0.0.5 is the linux-vm's Private IP address.

<img width="1182" height="639" alt="image" src="https://github.com/user-attachments/assets/42d4f634-c512-4158-9949-17406705147a" />

Clicked on Internet Message Control Protocol and clicked on Data. On the right you can see the payload or the actual chunk of data that was sent in the ping which starts with abcdefg

<img width="901" height="341" alt="image" src="https://github.com/user-attachments/assets/61aebf5c-b541-4837-9a04-6f800fa0db43" />

Clicked on ping reply packet from the linux-vm

<img width="444" height="307" alt="image" src="https://github.com/user-attachments/assets/c1ae42fc-50d7-4bb2-ae2d-82f7dc2829ce" />

Clicked on Internet Protocol and there shows the reply source from the linux-vm (10.0.0.5) to the destination windows-vm (10.0.0.4)

<img width="703" height="483" alt="image" src="https://github.com/user-attachments/assets/e283a846-92ec-4026-a119-f9f8422a6169" />

Typed ping 10.0.0.5 -t to ping the linux-vm nonstop 

<img width="891" height="673" alt="image" src="https://github.com/user-attachments/assets/85a76cc4-3cd3-45cf-abf6-948621700fbe" />

Powershell shows the nonstop pings to the linux-vm and Wireshark is capturing all of the nonstop pings happening.

<img width="370" height="267" alt="image" src="https://github.com/user-attachments/assets/fde90b2f-52df-4d75-9a8f-88d8ba0a9e1d" />

In Microsoft Azure clicked on linux-vm

<img width="646" height="314" alt="image" src="https://github.com/user-attachments/assets/dcf16b5a-b236-4e01-bbbd-f4977373f6f4" />

Clicked on Network settings under Networking. Under Network Security Group clicked on linux-vm-nsg

<img width="435" height="326" alt="image" src="https://github.com/user-attachments/assets/40c5f7cb-3d75-4a6e-80b4-49098bc72d3b" />

Clicked on Inbound Security Rules under Settings and clicked Add.

<img width="888" height="594" alt="image" src="https://github.com/user-attachments/assets/107df7c2-6587-440b-b500-56d4bf0bc078" />

For the Source selected Any, that comes from anywhere. Selected any Destination. For Destination Port ranges typed an asterisk meaning any because icmp does not use a port. Under Protocol selected ICMPv4 since ping uses ICMP protocol and clicked Deny action. Set the priority to 290 to make it the first rule to be evaluated first and then clicked Add.

<img width="824" height="183" alt="image" src="https://github.com/user-attachments/assets/13e6353b-1e3f-4c91-9c8f-7d8399a6e767" />

Security Rule shows ICMP traffic from any source to any destination will be denied.

<img width="463" height="483" alt="image" src="https://github.com/user-attachments/assets/bcf8d26a-0a8d-49b9-9b40-3961e121b9d8" />

With the Security Rule in effect, the pings in Powershell will say request timed out because the linux-vm is now ignoring those requests coming from the windows-vm.

<img width="957" height="374" alt="image" src="https://github.com/user-attachments/assets/f8202ce4-3771-47dc-b144-e358ca1540ad" />

In Wireshark there are only requests from the windows-vm saying no response found and no replies from the linux-vm because the firewall is blocking those requests.

<img width="854" height="282" alt="image" src="https://github.com/user-attachments/assets/cc7f2da7-9c16-4eec-941d-b5c0121feb55" />

Clicked delete and clicked yes to delete the Security Rule that was created.

<img width="1080" height="586" alt="image" src="https://github.com/user-attachments/assets/87f18cce-f0d4-4c0b-a5e0-dab759db85b7" />

Now in Powershell there are replies from the linux-vm and in Wireshark it also captured replies.

<img width="513" height="484" alt="image" src="https://github.com/user-attachments/assets/5eec566c-7dbb-4912-b296-83b4f1064dd0" />

Pressed ctrl + c to stop ping activity and closed Wireshark.

<h2>Observing ssh, DHCP </h2>

<img width="945" height="484" alt="image" src="https://github.com/user-attachments/assets/171b051f-628c-43e8-8690-057b0c19cdb8" />

From windows-vm opened Wireshark and clicked on Ethernet

<img width="359" height="79" alt="image" src="https://github.com/user-attachments/assets/68700a26-a297-4f87-9717-dbe1f2f1034d" />

Clicked on the blue icon to start capturing Network traffic

<img width="942" height="213" alt="image" src="https://github.com/user-attachments/assets/e9a1137e-f47b-43db-927b-56b6e497ee75" />

Typed ssh in the search box to filter for ssh traffic only

<img width="729" height="340" alt="image" src="https://github.com/user-attachments/assets/36c31839-b887-4e76-bfc2-05e2e927a65b" />

In Microsoft Azure clicked on linux-vm and copied its private IP address

<img width="1136" height="590" alt="image" src="https://github.com/user-attachments/assets/eebe4104-d56f-4063-83df-827db8d5e709" />

Back in the windows-vm opened Powershell and typed ssh labuser@10.0.0.5 and pasted the IP address and pressed Enter.

<img width="1127" height="607" alt="image" src="https://github.com/user-attachments/assets/df179745-ade6-41a6-8a04-22ba1dfc7e22" />

Typed Yes to continue connecting to the linux-vm and ssh traffic has been captured in Wireshark

<img width="710" height="485" alt="image" src="https://github.com/user-attachments/assets/d384bf8c-b545-4323-a99d-ce9d8a01db3f" />

Entered the linux-vm's password (Cyberlab123!) and pressed enter

<img width="663" height="482" alt="image" src="https://github.com/user-attachments/assets/3367e73f-e030-47ec-a4e4-0011edc2b317" />

The prompt changed to labuser@linux-vm which shows connection to the linux-vm was successful

<img width="638" height="480" alt="image" src="https://github.com/user-attachments/assets/fd52a485-f6a3-4bfc-8b97-dad08eb7498b" />

Typed id and it shows the username (labuser). Typed hostname and it shows the virtual machine's name (linux-vm). Typed uname -a and it shows details about the operating system.

<img width="1181" height="656" alt="image" src="https://github.com/user-attachments/assets/631a7084-bd65-4ef5-9140-6acea41a8f06" />

Typing even a single keystroke will cause Wireshark to capture it because traffic gets sent over the network by ssh. Every single keystroke gets sent to the linux-vm terminal and Wireshark captures it.

<img width="948" height="663" alt="image" src="https://github.com/user-attachments/assets/6349bd44-ce10-4645-ac68-7f7eb25a8d7a" />

Clicked on a packet and under SSH Protocol > SSH version 2 but you cant see the actual payload or chunk of data being sent because it is encrypted.

<img width="537" height="469" alt="image" src="https://github.com/user-attachments/assets/dd7bd9a9-7f17-45ea-9691-157218ff4378" />

Clicked on a packet that was from the windows-vm(10.0.0.4). Under Transmission Control Protocol there is the source port number and Destination port is 22 because ssh uses tcp port 22 to communicate.

<img width="538" height="455" alt="image" src="https://github.com/user-attachments/assets/ac1e8a5a-37f9-4f81-b17b-17b8c71d4c0d" />

Clicked on a packet from the linux-vm(10.0.0.5) and clicked Transmission Control Protocol. The source port is 22 and the Destination port is the windows-vm source port which shows that a packet is being sent to the windows-vm.

<img width="910" height="483" alt="image" src="https://github.com/user-attachments/assets/87f8d25a-3403-4625-853b-3cab9b0ce74a" />

In Powershell typed touch file.txt to create a file on the linux machine.

<img width="912" height="488" alt="image" src="https://github.com/user-attachments/assets/a66c8baf-c8f3-4ae8-ba04-7555e3dea9e4" />

Typed ls and it shows that the file was created

<img width="912" height="483" alt="image" src="https://github.com/user-attachments/assets/dbc2b62c-d595-46cd-98f3-e6cde018db7a" />

In Powershell typed exit to exit the SSH connection 

<img width="911" height="486" alt="image" src="https://github.com/user-attachments/assets/c5e46fa1-5d86-4f38-83f6-968869ad33e9" />

Typed hostname to check if logged out of the linux-vm successfully

<img width="1113" height="348" alt="image" src="https://github.com/user-attachments/assets/9de55219-80d6-4526-9cc9-82b09742acd9" />

In the red it shows a RST or a reset packet was sent from the wiwndows-vm(10.0.0.4) to the linux-vm(10.0.0.5) to kill the connection on port 22. Closed Wireshark and Powershell.

<img width="594" height="670" alt="image" src="https://github.com/user-attachments/assets/a6b930fc-1403-4510-bdc7-acfebbecbcbf" />

Opened Powershell and opened Wireshark. Clicked on Ethernet and started the network capture by clicking on the blue fin icon.

<img width="876" height="514" alt="image" src="https://github.com/user-attachments/assets/11720477-623a-4a42-b230-796d1583bce8" />

Opened notepad and typed ipconfig /release ipconfig /renew to create a script and run it in powershell to automatically release all of the IP addresses and to automatically request for a new IP address from DHCP.

<img width="232" height="167" alt="image" src="https://github.com/user-attachments/assets/fb0f37a6-bb2f-4229-853e-ec6bbc4d0a87" />

Clicked on file, save 

<img width="578" height="365" alt="image" src="https://github.com/user-attachments/assets/24530b17-21e4-4a6e-a3ec-c0db50323d2b" />

Save in This PC > Windows (C:) > ProgramData. Named the file dhcp.bat and saved as all files type.

<img width="324" height="112" alt="image" src="https://github.com/user-attachments/assets/44a5f7f2-a2ff-4ad2-9e30-61df83e72a62" />

Back in Wireshark filtered for DHCP traffic by typing udp.port == 67 || udp.port == 68

<img width="681" height="654" alt="image" src="https://github.com/user-attachments/assets/86710eb9-7660-475c-9dbd-bc974d8d8f1c" />

In Powershell typed cd C:/programdata and hit enter. Typed ls to see the list and dhcp.bat appears.

<img width="684" height="661" alt="image" src="https://github.com/user-attachments/assets/6cddf576-fc3d-4bb4-a1fb-467707984168" />

Typed ./dhcp.bat and hit enter for Powershell to run the script

<img width="1028" height="185" alt="image" src="https://github.com/user-attachments/assets/0a881bf5-6781-4275-b8db-d4bfbef62f09" />

In Wireshark the network traffic was captured. The release packet was sent from the windows-vm (10.0.0.4) to the DHCP Server
