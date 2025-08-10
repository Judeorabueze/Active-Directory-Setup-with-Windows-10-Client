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
- Chose the installation disk and clicked Next to begin installation

![unattended installation](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/unallocated%20space.png)

- After installation, set a secure Administrator password.

![password](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/set%20password.png)

- Hit Enter and the installation was completed.

![Finish](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/finish.png)

*Windows server 2019* 

- Enabled Shared Clipboard and Drag and Drop to Bidirectional in VirtualBox for easier file and text transfer between host and VM.
- Renamed the server name using the <b>Rename this pc</b> in the systems <b>Device specifications</b>.
- Restarted the system.

### 3. Configuring Active Directory Domain Services (AD DS)

To enable centralized management of the Windows 10 client, I installed and configured Active Directory Domain Services (AD DS) on the Windows Server 2019 virtual machine, promoting it to a Domain Controller.

- Logged into the Windows Server 2019 VM.
- Opened Server Manager, clicked Manage, and selected Add Roles and Features.
- Chose Role-based or feature-based installation and clicked Next.
- Selected the target server from the server pool and clicked Next.
- From the list of roles, selected Active Directory Domain Services (AD DS).
- Clicked Add Features when prompted to include required components, then clicked Next.
- Accepted the default features (including .NET Framework 3.5) and proceeded by clicking Next twice.
- Clicked Install and allowed the installation to complete.
- After installation, clicked Promote this server to a domain controller.
- Selected Add a new forest, entered the root domain name (e.g., mylab.local), and clicked Next.
- Set a Directory Services Restore Mode (DSRM) password and clicked Next.
- Accepted the automatically generated NetBIOS domain name (or shortened it if desired), then clicked Next.
- Reviewed configuration selections and clicked Next.
- After prerequisite checks passed, clicked Install.
- Allowed the system to complete the configuration and automatically restart, finalizing the promotion to Domain Controller.

At this stage, the server was successfully configured as a Domain Controller with Active Directory services ready to manage network clients.



