#Core2
The user can also display help on a particular command by using the /? switch.

The robocopy command (or "robust copy") is another file copy utility. Microsoft now recommends using robocopy rather than xcopy. For example, robocopy works better with long file names and New Technology File System (NTFS) attributes.

The Windows Resource Protection mechanism prevents damage to, or malicious use, of system files and registry keys and files. In addition, the System File Checker utility (sfc) provides a manual interface for verifying system files and restoring them from the cache if found corrupt or damaged.

![[Pasted image 20231110131907.png]]
![[Pasted image 20231110134202.png]]

SUSE and Red Hat are subscription-based. Originally developed by Linus Torvalds, Linux is a fully open-source OS kernel derived from UNIX.

A Windows administrator wants to become more familiar with Linux but still wants to use Windows primarily. The administrator installs the bash subsystem for Windows and is reading about how Windows has made strides to become more compatible with Linux. Which of the following was part of the changes to the underlying New Technology File System (NTFS) structure?
	To support UNIX/Linux compatibility, Microsoft engineered the New Technology File System (NTFS) to support case-sensitive naming, hard links, and other key features UNIX/Linux applications require.

A server administrator tests an application migration from a 32-bit server to a 64-bit server, but the application is still 32-bit. Where will Windows run the application?
	In 64-bit Windows, the applications run within a special application environment called WOW64 (Windows on Windows 64-bit). This environment replicates the 32-bit environment expected by the application and translates its requests into ones that can be processed by the 64-bit CPU, memory, and file subsystems.

A curious IT professional investigates the hidden System Reserved partition. What will the professional find contained in the partition?
	The BOOTMGR and the boot configuration data (BCD) file are normally installed to a hidden System Reserved partition.

**Extensible Authentication Protocol over Wireless (EAPoW)** is a protocol used for wireless network authentication. It allows for a variety of authentication methods to be used over wireless networks. When implementing EAPoW, the network professional will need to configure an authentication server that supports EAP methods, and this is often done using **Active Directory** (AD).  Active Directory is a directory service developed by Microsoft that provides centralized authentication, authorization, and directory services. It's commonly used for user authentication in enterprise environments, and it can be integrated with various EAP methods to provide secure and centralized authentication for wireless networks.

A user finds that their home computer fails to boot. The user believes part of the operating system (OS) is corrupted. They want to recover it but do not want to lose any personal documents. What should the user do?
	Using refresh recopies the system files and reverts most system settings to the default but can preserve user personalization settings, data files, and apps installed via the Windows Store.

A server administrator wants to keep up with security patches and points their machines to pull updates. What should the administrator point towards?
	Copies of distribution packages (including any updates) will be posted to a software repository. Often the vendor will maintain different repositories. It can then be used to install, uninstall, or update the software.

After downloading a new application from the internet, a user drags the .app directory from their Downloads folder to their Applications folder on their Mac. What action did the user most likely perform?
	When the app has been installed, it is placed in a directory with a .app extension in the Applications folder.

A security analyst is looking at the overall security status of systems on the network. Which of the following represents the greatest risk?
	A legacy or end of life (EOL) system is one where the software vendor no longer provides support or fixes for problems. These represent the greatest risk to the network.

A network administrator is setting up administrative access to network devices. What common solution is used for this?
	TACACS+ is an AAA protocol like RADIUS, but it is typically used for device administration rather than user access to the network.

A network manager for a growing coffee company sets up wireless access points at cafe locations for users. The manager wants to set up access to allow anyone in the vicinity to join without a password but also make it as secure as possible. Which standard introduced this ability?
	In WPA2, Wi-Fi Enhanced Open traffic is unencrypted. WPA3 encrypts this traffic. This means that any station can still join the network, but traffic is protected against sniffing.

A security manager at a top-secret facility assesses the feasibility of integrating biometric authentication but has heard that it is often not accurate. Which of the following is the most accurate form of biometrics?
	Retinal scanning is one of the most accurate forms of biometrics. Retinal patterns are very secure, but the equipment required is expensive and the process is relatively intrusive and complex.

Mobile OS vendors use this "walled garden" model of software distribution as well. Apps are distributed from an approved store, such as Apple's App Store or the Windows Store.

A security manager sets up a defense in depth mechanism and sets up monitoring to catch communications from the attacker to the malware. What is the manager monitoring for?
	Whether a backdoor is used as a standalone intrusion mechanism or to manage bots, the threat actor must establish a connection from the compromised host to a command and control (C2 or C&C) host or network.

A Firefox user wants to open up their browser settings to configure their intranet as the home page. How can the Firefox user access the settings?
	about:preferences

A user's phone is randomly rebooting all the time. What should the user do first to diagnose the issue?
	A device that randomly reboots might be overheating, having a low battery charge, or having a faulty battery or other hardware.

A security analyst analyzes how most attackers perform exploits against iOS operating systems. Which of the following is most applicable?
	For most exploits, this can only be done when the device is attached to a computer while it boots (tethered jailbreak).

A security manager is looking at mobile security for company devices. They are investigating no-root firewalls and understanding how this works. Which of the following best describes no-root firewalls?
	"No-root" firewalls work by creating a virtual private network (VPN) and then controlling app access to the virtual private network (VPN).

Email data and any apps using the "Data Protection" option are subject to a second round of encryption using a key derived from and protected by the user's credential.

A Windows administrator is combing through server logs and sees that a wscript.exe executed a script. What type of script is executed by default?
	VBScript files are identified by the .VBS extension. VBScript is executed by the wscript.exe interpreter by default.

A user at a large organization notices that their computer is extremely sluggish. This happened shortly after the user clicked on a link in an email that seemed suspicious. Where should the user most likely report this to?
	Larger organizations will provide a dedicated Computer Security Incident Response Team (CSIRT) as a single point of contact so that a security incident can be reported through the proper channels.

A security engineer wants to learn how to code in Python but is running a Windows box. Which of the following is the easiest interpreter to set up for Windows?
	CPython is the simplest environment to set up for Windows. When using CPython in Windows, there is a console interpreter (python.exe) and a windowed interpreter (pythonw.exe).

A server administrator is setting up a backup program for the servers to ensure recovery. Which of the following are the two main principles of backing up? (Select all that apply.)
	Frequency
	Retention

### 3-2-1 Backup Rule

The 3-2-1 backup rule is a best-practice maxim that you can apply to your backup procedures to verify that you are implementing a solution that can mitigate the widest possible range of disaster scenarios. It states that you should have three copies of your data (including the production copy), across two media types, with one copy held offline and off site.

A company's threat intelligence team determines that one of a threat actor's techniques is to perform a denial of service against the Remote Desktop Protocol (RDP) functionality in servers. What can the company enable to help prevent this?
	Network Level Authentication (NLA) protects the Remote Desktop Protocol (RDP) server against denial of service attacks. Without NLA, the system configures a desktop before the user logs on.

A security analyst working on a monitoring team wants to implement new monitoring mechanisms around Secure Shell (SSH) authentication. Which of the following should the analyst focus on?
	Monitoring for and removing compromised client public keys is a critical security task. Many recent attacks on web servers have exploited poor SSH key management.

Remote network boot capability is often referred to as wake on LAN (WOL) and allows devices to be remotely powered on over a network.

In a Windows batch file, the net use command performs drive mapping. Network drive mapping is a Windows-only concept.

A user experiences issues with their computer and has asked someone to remote desktop onto their computer to help resolve the issue. Unfortunately, the firewall only allows port 443 traffic. What should they use for assistance?
	Quick Assist works over the encrypted HTTPS port TCP/443. The helper must be signed in with a Microsoft account to offer assistance.

A user accidentally deleted the presentation they were working on for an important upcoming meeting. Where should the user go for help?
	In Windows, user data backup options are implemented via the File History feature, which is accessed through Settings > Update & Security > Backup.

A data center technician receives the latest shipment, but it includes some hazardous materials. What should the technician check first?
	Some hazard information will be provided on labels, but the supplier must also provide more detailed information on an SDS (Safety Data Sheet).

# Test problems

A company has several offices within the United States. Engineers look to configure Microsoft DirectAccess virtual private networking technology for remote connections. Engineers instruct IT to deploy which operating system to Windows desktops?
	Windows Enterprise edition has several features that are not available in the Pro edition, such as support for Microsoft’s DirectAccess virtual private networking technology.

How might a mobile-device management suite of software detect that a user has rooted an Android device?
	1. There is no valid developer code signature.

A network engineer implements a proxy at a small company. The configuration does not require settings on every client machine. What type of proxy does the engineer deploy? (Select all that apply.)
	1. Transparent   
    Intercepting

![[Pasted image 20231117142309.png]]
Domain Controllers: OU

A Windows user is not able to resolve server names on a local network. After updating the system’s hosts file, which command does the user issue?
	The domain name system (DNS) is used to resolve IP addresses to host names. Whether a server or a hosts file is used, the ipconfig /flushdns command clears a system’s DNS cache.

A Windows user runs the Performance Monitor tool to check disk activity. What counter is the best option the user can evaluate to understand how busy the disk is at any given time?
	The % disk time metric is the percentage of elapsed time that the selected disk drive is busy servicing read or write requests.

A technician would like to set every Windows computer at an organization to have a company logo as a desktop wallpaper. What does the technician determine as the best method for deploying the setting?
	A domain group policy configures computer settings and user profile settings for all computers and user accounts within a domain. This type of policy would satisfy the requirement.

A user suspects that a USB drive on their system has been tampered with. The user begins using the drive by saving a few reports while waiting for an IT technician to investigate. What does the user compromise?
	Data integrity refers to the authorized or unauthorized manipulation of data. This also applies to intentional or unintentional manipulation. Contents of the drive may be useful as evidence.

A user installs an application on a macOS device. The user determines that installation will require running an additional service. What installer format does the application use?
	The macOS pkg format is used where app setup needs to perform additional actions, such as running a service or writing files to multiple folders.

![[Pasted image 20231117142522.png]]

A tech has an Android tablet that no longer receives updates due to its age. Learning that a custom firmware with new features is available, what does the tech require to install the image?
	For some devices, it is necessary to exploit a vulnerability or use custom firmware. Custom firmware is essentially a new Android OS image applied to the device and requires root access to install.

A technician configures a backup routine on an important workstation. Which type does the routine use when only backing changes since the last full backup?
	Differential jobs select new files and files modified since the original full job. A differential chain has moderate time and storage requirements.

A computer security team investigates a high-level computer breach at a large company. While investigating one of the computers in question, the team finds a USB drive inserted into the back of the shared user desktop tower. What are the primary concerns for the team from this discovery related specifically to the USB drive found? **(Select all that apply.)**
	Chain of Custody refers to the sequence of custody, control, transfer, analysis, and disposition of evidence. It is crucial to maintain a record to show who has had control of the evidence to ensure its integrity and admissibility in court. In this case, the USB drive could be critical evidence, so maintaining its chain of custody is essential.  
	Data Integrity refers to the authorized or unauthorized manipulation of data. Digital information is susceptible to tampering, especially when it is easily accessible via an unsecured USB drive plugged into a computer. The team must ensure that the data on the drive hasn't been altered in any unauthorized way.

A user looks to reconfigure an IP address for a network adapter. Which Control Panel applet is the most direct?
	Network Connections (ncpa.cpl) is a Control Panel applet for managing adapter devices, including IP address information.

A tech firm deploys wireless installations at client sites. As the firm uses Wi-Fi Protected Access (WPA) version 3, which security technology does the deployment utilize? (Select all that apply.)
	Simultaneous Authentication of Equals (SAE) in WPA3 replaces the 4-way handshake in WPA2. The 4-way handshake mechanism is vulnerable to manipulations that allow a threat actor to recover the key.
	WPA3 replaces Advanced Encryption Standard Counter Mode with Cipher Block Chaining Message Authentication Code Protocol with the stronger AES Galois Counter Mode Protocol (GCMP) mode of operation.

A user needs to restore a problematic Windows system to its original factory state. What approach does the user utilize to achieve the restoration?
	A factory recovery partition is a tool used by the original equipment manufacturers (OEMs) to restore the OS environment to its ship state. The recovery partition is created on the internal fixed drive.

A recent software installation on a Windows desktop fails. Which internal log file does a technician review to see what may have gone wrong?
	The application log contains information regarding non-core processes and utilities for some third-party applications. Third-party application installers write events to the application log.

A problematic Windows system with multiple operating systems installed does not boot properly. A support technician tries to diagnose by outlining the boot process. The technician determines that the system uses an Extensible Firmware Interface (EFI) system partition. Which file does the technician inspect for problems related to a specific operating system boot problem?
	The GUID partition table (GPT) identifies a System Partition. The system partition contains the boot manager and the boot configuration data (BCD). Each Windows installation has a subfolder under \EFI\Microsoft\ that contains a BCD and BOOTMGFW.EFI.

![[Pasted image 20231117142933.png]]

A Windows user runs the Defragment and Optimize Drives tool (dfrgui.exe) on a solid state drive (SSD). What action will the tool take on the drive? (Select all that apply.)
	On a solid state drive (SSD), data is stored in units called blocks that are not directly managed by the OS. The tool runs a trim process that identifies data that the OS has marked as deletable.
	When the tool initiates a trim, data that is marked as deletable ultimately has its occupied blocks tagged as writable.

A computer user looks to map a network drive using the most basic scripting language possible. Which language does the user implement for a Windows system?
	Windows PowerShell (PS) combines a script language with hundreds of prebuilt modules called cmdlets that can access and change most components and features of Windows and Active Directory.

A Windows 7 computer user requires help from the IT department. A technician instructs the user to create an invitation file. What type of Windows help session does the user create?
	Microsoft Remote Assistance (MSRA) allows a user to ask for help from a technician or co-worker via an invitation file protected by a passcode.

A user wishes to enable multiple desktops within macOS for different work environments. What feature makes this possible?
	The Mission Control feature is used for window management and enables the user to set up multiple desktops with different sets of apps and backgrounds.

# ExamCompass

list directories: dir, dir * . *
make dir: mkdir, md
display current computer: hostname
Netstat: active TCP/IP connections, Network protocol statistics
net use :for computer connections to shared resources
shutdown :shutdown local or remote host
sfc :scans integrity of protected files and replaces incorrect versions
diskpart :cml partitioning utility
pathping :features of ping and tracert

   


