# Active Directory Setup with Windows Client

## Introduction

This project demonstrates the installation and configuration of a Windows Server 2019 Domain Controller and the integration of a Windows 10 client into an Active Directory environment.
The setup was carried out in a virtualized lab using Oracle VirtualBox, simulating a real-world enterprise network.

Key tasks included deploying Active Directory Domain Services (AD DS), configuring DNS, creating domain users, and joining a client machine to the domain for centralized authentication and management.

## Objectives

- Install and configure Windows Server 2019 as a Domain Controller.
- Set up Active Directory Domain Services and create a new forest/domain.
- Configure DNS to support domain operations.
- Join a Windows 10 client to the newly created domain.
- Apply real-world troubleshooting techniques for installation and network issues.

## Tools & Technologies Used

- Oracle VirtualBox
- Windows Server 2019 (Datacenter Evaluation – Desktop Experience)
- Windows 10 (Client)
- Active Directory Domain Services
- DNS Server
- Command-line Networking Tools (ipconfig, ping, nslookup, etc.)

## Implementation Steps

### 1. VirtualBox and Windows 10/11 Installation
-	Visited the VirtualBox official website https://www.virtualbox.org/wiki/Downloads
-	Selected the appropriate VirtualBox platform package (In my case, Windows) 
-	Clicked the host (Windows) and allow to download.
-	Double-clicked on the downloaded Oracle VirtualBox installation file and start the installation.
-	See step by step guide in the [Windows-11-Virtual-Homelab-Setup](https://github.com/Judeorabueze/Windows-11-Virtual-Homelab-Setup)

### 2. Installing Windows Server 2019

- Navigated to the Windows Server 2019 Evaluation Center via Google search or directly at https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019.
- Completed the Register for Free Trial form.
- Selected Windows Server 2019 (English ISO 64-bit edition).

![Windows Server](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Windows%20server.png)

- Downloaded the ISO file and waited for completion.
- Opened Oracle VirtualBox and created a new virtual machine by clicking Tools → New.

![Windows server vm](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Virtual%20Machine%20name.png)

- In the Name and Operating System section, entered Domain Controller DC and selected the appropriate OS type and version.
- Under ISO Image, uploaded the downloaded ISO file.
- Skipped the Unattended Installation option.
- Allocated hardware resources (CPU, RAM, storage) based on host system capacity and available space.
- Clicked Finish to create the virtual machine.

![Domain Controller](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Domain%20controller.png)

- Right-clicked the newly created Domain Controller VM, went to Settings → System, and unchecked Floppy from the boot order to ensure the VM booted from the ISO.

![boot](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/System%20boot.png)

- Under Network, changed the adapter type from NAT to Bridged Adapter to allow the VM to obtain network access from the host system.

![bridge adapter](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Bridge%20adapter.png)

- Clicked OK and started the Domain Controller VM.
- Selected the preferred language and clicked Install Now.

![install now](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/install%20now.png)

- Chose Windows Server Datacenter Evaluation (Desktop Experience) as the edition.

![Windoes server edition](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/server%20operating%20system.png)

- Accepted the license terms.
- Selected Custom: Install Windows Only for a fresh installation.
- Chose the installation disk and clicked Next to begin installation.
- After installation, set a secure Administrator password.

Enabled Shared Clipboard and Drag and Drop to Bidirectional in VirtualBox for easier file and text transfer between host and VM.
