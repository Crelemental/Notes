# Configuring Windows

It can also be used to change the User Account Control (UAC) settings. UAC is a system to prevent unauthorized use of administrator privileges. At the default setting level, changing an administrative setting requires the user to confirm a prompt or input the credentials for an administrator account.

### Indexing Options

You can configure file search behavior on the **Search** tab of the File Explorer Options dialog. Search is also governed by settings configured in the **Indexing Options** applet. This allows you to define indexed locations and rebuild the index. Indexed locations can include both folders and email data stores. A corrupted index is a common cause of search problems.

### Power
The Advanced Configuration and Power Interface (ACPI) specification is designed to ensure software and hardware compatibility for different power-saving modes. There are several levels of ACPI power mode, starting with S0 (powered on) and ending with S5 (soft power off) and G3 (mechanically powered off). In between these are different kinds of power-saving modes:
- Standby **/Suspend to RAM**—Cuts power to most devices (for example, the CPU, monitor, disk drives, and peripherals) but maintains power to the memory. This is also referred to as ACPI modes S1–S3.
- Hibernate **/Suspend to Disk**—Saves any open but unsaved file data in memory to disk (as hiberfil.sys in the root of the boot volume) and then turns the computer off. This is also referred to as ACPI mode S4.

You can also enable **Universal Serial Bus (USB) selective suspend** to turn off power to peripheral devices.

### Admin tools
A Microsoft Management Console (MMC) contains one or more snap-ins that are used to modify advanced settings for a subsystem, such as disks or users. The principal consoles available via Administrative Tools are:
* ***Computer Management (compmgmt.msc)**—The default management console with multiple snap-ins to schedule tasks and configure local users and groups, disks, services, devices, and so on.
- **Defragment and Optimize Drives (dfrgui.exe)**—Maintain disk performance by optimizing file storage patterns.
- **Disk Cleanup (cleanmgr.exe)**—Regain disk capacity by deleting unwanted files.
- **Event Viewer (eventvwr.msc)**—Review system, security, and application logs.
- **Local Security Policy (secpol.msc)**—View and edit the security settings.
- **Resource Monitor (resmon.exe)** and **Performance Monitoring (perfmon.msc)**—View and log performance statistics.
- **Registry Editor (regedit.exe)**—Make manual edits to the database of Windows configuration settings.
- **Services console (services.msc)**—Start, stop, and pause processes running in the background.
- **Task Scheduler (taskschd.msc)**—Run software and scripts according to calendar or event triggers.


# Managing Windows

### Disk Maintenance
- **Fragmentation**—On a hard disk, ideally each file would be saved in contiguous clusters on the disk. In practice, over time as files grow, they become fragmented across non-contiguous clusters, reducing read performance.
- **Capacity**—Typically, much more file creation occurs on a computer than file deletion. This means that capacity can reduce over time. If the boot volume has less than 20% free space, performance can be impaired. When space drops below 200 MB, a Low Disk Space warning is generated.
- **Damage**—Hard disk operations are physically intensive, and the platters of the disk are easy to damage, especially if there is a power cut. If the disk does not recognize that a sector is damaged, files can become corrupted. SSDs can suffer from degradation of the memory circuitry, resulting in bad blocks, and can be damaged by impacts, overheating, and electrical issues.

### Disk Defragmenter
The **Defragment and Optimize Drives tool (dfrgui.exe)** runs various operations to speed up the performance of HDDs and SSDs:
- On an HDD, defragmenting rewrites file data so that it occupies contiguous clusters, reducing the amount of time the controller has to seek over the disk to read a file.
- On an SSD, data is stored in units called blocks that are not directly managed by the OS. The drive controller determines how blocks are used according to wear-leveling routines to minimize degradation of the solid-state cells. The main purpose of the optimizer tool is to instruct the controller to run a TRIM operation. Essentially, TRIM is a process by which the controller identifies data that the OS has marked as deletable and can then tag corresponding blocks as writable. The optimizer does perform a type of defragmentation operation on an SSD if it holds the OS and the system protection feature Volume Shadow Copy service is enabled.

### Memory Monitoring
The **Memory** page reports which slots have modules installed and the speed. The usage statistics are broken down as follows:

- **In use** refers to system (RAM) usage only.
- **Committed** reports the amount of memory requested and the total of system plus paged memory available. Paged memory refers to data that is written to a disk pagefile.
- **Cached** refers to fetching frequently used files into memory pre-emptively to speed up access.
- **Paged pool** and **non-paged pool** refer to OS kernel and driver usage of memory. Paged usage is processes that can be moved to the pagefile, while non-paged is processes that cannot be paged.

### In Performance Monitor, 
you can create log files, referred to as Data Collector Sets, to record information for viewing later. You can generate a library of performance measurements taken at different times of the day, week, or even year. This information can provide a system baseline and then be used to give a longer-term view of system performance.

There are two types of logs: counter and trace:

- Counter logs allow you to collect statistics about resources, such as memory, disk, and processor. These can be used to determine system health and performance.
- Trace logs can collect statistics about services, providing you with detailed reports about resource behavior. In essence, trace logs provide extensions to the Event Viewer, logging data that would otherwise be inaccessible.

### msconfig.exe
The **Boot** tab lets you configure basic settings in the Boot Configuration Data (BCD) store. You can change the default OS, add boot options (such as Safe Mode boot) with minimal drivers and services, and set the timeout value—the duration for which the boot options menu is displayed. To add boot paths, you have to use the bcdedit command.


# Identifying OS Types and Features

- **Network Operating System (NOS)**—An OS designed to run servers in business networks.

**UNIX** is a trademark for a family of operating systems originally developed at Bell Laboratories in the late 1960s. All UNIX systems share a kernel/shell architecture. The kernel is the low-level code that mediates access to system resources (CPU, RAM, and input/output devices) for other processes installed under the OS. Interchangeable shells run on the kernel to provide the user interface.

Examples of notable distros include SUSE, Red Hat, Fedora, Debian, Ubuntu, Mint, and Arch. Distros can use different licensing and support options. For example, SUSE and Red Hat are subscription-based, while Ubuntu is free to install but has paid-for enterprise support contracts, and Fedora, Debian, Mint, and Arch are community supported.

### Windows File Systems
The **New Technology File System (NTFS)** is a proprietary file system developed by Microsoft for use with Windows. It provides a 64-bit addressing scheme, allowing for very large volumes and file sizes. In theory, the maximum volume size is 16 Exabytes, but actual implementations of NTFS are limited to between 137 GB and 256 Terabytes, depending on the version of Windows and the allocation unit size. The key NTFS features are:

- **Journaling**—When data is written to an NTFS volume, it is re-read, verified, and logged. In the event of a problem, the sector concerned is marked as bad and the data relocated. Journaling makes recovery after power outages and crashes faster and more reliable.
- **Snapshots**—This allows the Volume Shadow Copy Service to make read-only copies of files at given points in time even if the file is locked by another process. This file version history allows users to revert changes more easily and also supports backup operations.
- **Security**—Features such as file permissions and ownership, file access audit trails, quota management, and encrypting file system (EFS) allow administrators to ensure only authorized users can read/modify file data.
- **POSIX Compliance**—To support UNIX/Linux compatibility, Microsoft engineered NTFS to support case-sensitive naming, hard links, and other key features required by UNIX/Linux applications. Although the file system is case-sensitive capable and preserves case, Windows does not insist upon case-sensitive naming.
- **Indexing**—The Indexing Service creates a catalog of file and folder locations and properties, speeding up searches.
- **Dynamic Disks**—This disk management feature allows space on multiple physical disks to be combined into volumes.

FAT32 does not support any of the reliability or security features of NTFS. It is typically used to format the system partition (the one that holds the boot loader). It is also useful when formatting removable drives and memory cards intended for multiple operating systems and devices.

exFAT is a 64-bit version of FAT designed for use with removable hard drives and flash media. Like NTFS, exFAT supports large volumes, up to a recommended maximum size of 512 Terabytes (TB). There is also support for access permissions but not encryption.

### LINUX and MacOS File Systems
Most Linux distributions use some version of the extended (ext) file system to format partitions on mass storage devices. **ext3** is a 64-bit file system with support for journaling. **ext4** delivers better performance than ext3 delivers and would usually represent the best choice for new systems.

Apple Mac workstations and laptops use the proprietary **Apple File System (APFS)** , which supports journaling, snapshots, permissions/ownership, and encryption.

### Licensing
- Windows Pro is designed for small and medium-sized businesses and can be obtained using OEM or retail licensing. This "Professional" edition comes with management features designed to allow network administrators more control over each client device. There is also a Pro for Workstations edition with support for more advanced hardware.
- Windows Enterprise has the full feature set but is only available via volume licensing.
- Windows Education/Pro Education are variants of the Enterprise and Pro editions designed for licensing by schools and colleges.

Windows Pro for Workstations has the same features as Pro but supports more maximum RAM and advanced hardware technologies, such as persistent system RAM (NVDIMM).

The Pro/Enterprise/Education editions of Windows have less restrictive hardware limits than those of the Home edition. They all support computers with multiple processors:

- Pro and Education editions support 2-way multiprocessing and up to 128 cores.
- Pro for Workstations and Enterprise editions support 4-way multiprocessing and up to 256 cores.

They have the following system RAM support limitations:

- Pro and Education editions are restricted to 2 TB.
- Pro for Workstations and Enterprise editions are restricted to 6 TB.


# Supporting Windows

Microsoft maintains a Windows Logo'd Product List (LPL) catalog, previously called the Hardware Compatibility List (HCL). This is a catalog of tested devices and drivers. If a device has not passed Windows logo testing, you should check the device vendor's website to confirm whether there is a driver available.

An unattended installation uses a script or configuration file to input the choices and settings that need to be made during setup. In Windows, this is referred to as an answer file.

Unattended installations are also often completed using **image deployment**. An image is a clone of an existing installation stored in one file. The image can contain the base OS and configuration settings, service packs and updates, applications software, and whatever else is required. An image can be stored on DVD or USB media or can be accessed over a network. Using image deployment means that machines use a consistent set of software and configuration options.

Most computers now come with a **Preboot eXecution Environment (PXE)** –compliant firmware and network adapter to support this boot option. The client uses information provided via a Dynamic Host Configuration Protocol (DHCP) server to locate a suitably configured server that holds the installation files or images and starts the setup process.

Information about partitions is stored on the disk itself in one of two types: master boot record (MBR) or GUID [globally unique identifier] Partition Table (GPT).

A factory **recovery partition** is a tool used by OEMs to restore the OS environment to its ship state. The recovery partition is created on the **internal fixed drive** 


# Managing Windows Networking
### Manage Windows Networking
When you connect to a new network, the Network Location Awareness (NLA) service prompts you to set the network profile type. If the network profile type is set as Private, the PC is discoverable and may be used for folder or printer sharing. This is only advisable when connecting to a trusted network. If the network is set as Public, Windows Firewall is configured to block all access and make the host undiscoverable.

### Troubleshoot Windows Networking
- **Limited connectivity**—The adapter is set to obtain an address automatically, but no DHCP server can be contacted. The adapter will either use an address from the automatic IP addressing (APIPA) 169.254.x.y range or will use an address specified as an alternate configuration in IPv4 properties.

If a DHCP lease is missing or incorrect, you can use ipconfig to request a new one.

- Release the IP address obtained from a DHCP server so that the network adapter(s) will no longer have an IP address:

ipconfig /release _AdapterName_

- Force a DHCP client to renew the lease it has for an IP address:

ipconfig /renew _AdapterName_

You can also use ipconfig to troubleshoot some issues with resolving name records via DNS:

- Display the DNS resolver cache. This contains host and domain names that have been queried recently. Caching the name-to-IP mappings reduces network traffic:

ipconfig /displaydns

- Clears the DNS resolver cache. If cached records are out-of-date, it can cause problems accessing hosts and services:

ipconfig /flushdns
### Configure Windows Security Settings
- A **local account** is defined on that computer only. For example, PC1\David is the username for an account configured on a host named PC1. A local user account is stored in a database known as the Security Account Manager (SAM), which is part of the HKEY_LOCAL_MACHINE registry. Each machine maintains its own SAM and set of SIDs for accounts. Consequently, a local account cannot be used to log on to a different computer or access a file over the network.

### Manage Security Shares
- **Roaming profiles** copies the whole profile from a share at logon and copies the updated profile back at logoff. Roaming profiles are enabled by entering the path to a share in the **Profile** path box in the general form \\SERVER\ROAMING$\%USERNAME% . The main drawback is that if a profile contains a lot of large data files, there will be a big impact on network bandwidth and sign-in and sign-out performance will be slow.

#Core2