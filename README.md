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
- Chose the installation disk and clicked <b>Next</b> to begin installation

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
- On the <b>Server Manager Dashboard</b>, clicked <b>Manage</b>, and selected <b>Add Roles and Features</b>.

![Server manager](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Server%20manager%20dashboard.png)
  
- On the <b> Add Roles and Features Wizard</b> box, chose <b>Role-based or feature-based installation</b> and clicked Next.

![Installation type](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/installation%20type.png)

- Selected the target server from the server pool and clicked Next.
- From the list of roles, selected <b>Active Directory Domain Services (AD DS)</b>.

![Active Directory](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Active%20directory%20domain%20services.png)

- Clicked <b>Add Features</b> when prompted to include required components, then clicked Next.
- Accepted the default features (including .NET Framework 3.5) and proceeded by clicking Next twice.
- On the <b>Confirm installation selections</b> dialogue box, clicked <b>Install</b>.

![netframe](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/.netframe.png)

- Allowed the installation to complete.

![installation progress](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Installation%20progress.png)

- After installation, clicked <b>Promote this server to a domain controller</b>.
- On the <b>Active Directory Domain Service Wizard</b>, selected <b>Add a new forest</b>, entered the <b>root domain name</b> (i used my name - judeorabueze.com), and clicked Next.

![Active directory](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/deployment%20configuration.png)

- Set a <b>Directory Services Restore Mode (DSRM) password</b> and clicked Next.

![password](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Password.png)

- Accepted the automatically generated NetBIOS domain name (or shortened it if desired), then clicked Next.

![netbios](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Netbios.png)

- Reviewed configuration selections and clicked Next.
- After prerequisite checks passed, clicked Install.

![install](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/Install.png)

- Allowed the system to complete the configuration and automatically restart, finalizing the promotion to Domain Controller.

![DC](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/DC.png)

At this stage, the server was successfully configured as a Domain Controller with Active Directory services ready to manage network clients.

### 4. Creating a Domain User Account

After configuring the Domain Controller, I created a new user account within Active Directory for demonstration and testing purposes.

- Logged into the Domain Controller and opened Server Manager.
- Clicked on <b>Tools</b> and selected <b>Active Directory Users and Computers (ADUC)</b>.

![Active Directory User](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/AD%20Tools.png)

- Expanded the root domain (in this lab: judeorabueze.com) and selected the <b>Users</b> container.
- Right-clicked within the <b>Users</b> container, selected <b>New → User</b>.

![Users Container](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/domain%20user.png)

- Entered the required details in the <b>New Object</b> – User window.

![new object](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/New%20object%20user.png)

- Clicked <b>Next</b> and created a secure password for the account.

![Password](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/New%20user%20password.png)

- Confirmed the password settings and clicked <b>Next</b> again.

![finish](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/New%20user%20finish.png)

- Reviewed the details and clicked <b>Finish</b> to create the account.

![confirmation](https://github.com/Judeorabueze/Active-Directory-Setup-with-Windows-10-Client/blob/main/New%20user%20confirmation.png)

*The new user account, Helpdesk Demo, was successfully created and added to the domain.*

### 5. Joining the Windows Client to the Domain

##### On the Domain Controller machine
- Opened the system command prompt (CMD)
- Entered the command `ipconfig`
- Took note of the IP address and network details of the Domain Controller.

#### On the Windows Client

- Renamed the Windows 10 client to a descriptive name for easier identification within the domain.
- On the Windows 10 (HelpDesk) client, right-clicked the network adapter icon and selected Open Network & Internet Settings.
- Clicked Change adapter options, then right-clicked Ethernet and selected Properties.
- Highlighted Internet Protocol Version 4 (TCP/IPv4) and clicked Properties.
- Selected Use the following DNS server addresses and entered the Domain Controller’s IP address as the Preferred DNS server.
- Entered the IP address, subnet mask, and default gateway to match the Domain Controller’s network configuration. This ensured the client was correctly pointed to the Domain Controller.
- Clicked OK to save changes.
- With the network configured, I proceeded to join the client to the domain:
- On the Windows 10 client, right-clicked the Start button and selected System.
- In the About window, clicked Advanced System Settings.
- In System Properties, navigated to the Computer Name tab and clicked Change.
- Selected Domain and entered the configured domain name (e.g., mylab.local).
- When prompted, entered the domain administrator’s username and password.
- Received confirmation that the computer was successfully added to the domain.
- Restarted the client to apply the changes.

The Windows 10 client was now successfully joined to the Active Directory domain and ready for domain-based management.
