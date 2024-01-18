#Core2
# Managing Security Settings
If the malware can be delivered as the payload for an exploit of a severe vulnerability, it may be able to execute without requiring any authorization using SYSTEM privileges. Alternatively, the malware may be able to use an exploit to escalate privileges after installation. Malware running with this level of privilege is referred to as a **rootkit** . The term derives from UNIX/Linux where any process running as root has unrestricted access to everything from the root of the file system down.

1. Investigate and verify malware symptoms.
2. Quarantine infected systems.
3. Disable System Restore in Windows.
4. Remediate infected systems:
    1. Update anti-malware software.
    2. Scanning and removal techniques (e.g., safe mode, preinstallation environment).
5. Schedule scans and run updates.
6. Enable System Restore and create a restore point in Windows.
7. Educate the end user.

# Supporting Mobile Software

# Implementing Operational Procedures
### Remote Desktop Protocol

Windows uses the **Remote Desktop Protocol (RDP)** to implement terminal server and client functionality. To connect to a server via Remote Desktop, open the **Remote Desktop Connection** shortcut or run mstsc.exe . Enter the server's IP address or fully qualified domain name (FQDN). Choose whether to trust the server connection, inspecting any certificate presented, if necessary.

### Virtual Network Computing

There are alternatives to using RDP for remote access. For example, in macOS, you can use the Screen Sharing feature for remote desktop functionality. Screen Sharing is based on the **Virtual Network Computing (VNC)** protocol. You can use any VNC client to connect to a Screen Sharing server.

VNC itself is a freeware product with similar functionality to RDP. It works over TCP port 5900. Not all versions of VNC support connection security. macOS Screen Sharing is encrypted.

### Microsoft Remote Assistance

**Microsoft Remote Assistance (MSRA)** allows a user to ask for help from a technician or co-worker via an invitation file protected by a passcode. The helper can open the file to connect over RDP and join the session with the user. There is a chat feature, and the helper can request control of the desktop.

### Monitoring
There are two general classes of tools that provide this type of enterprise monitoring and remote access:

- **Remote monitoring and management (RMM)** tools are principally designed for use by managed service providers (MSPs). An MSP is an outsourcing company that specializes in handling all IT support for their clients. An RMM tool will be able to distinguish client accounts and provide support for recording and reporting billable support activity.
- **Desktop management** unified endpoint management (UEM)/mobile-device management (MDM) suites are designed for deployment by a single organization and focus primarily on access control and authorization.
### Backup Chains

The requirements for backup frequency and retention must be managed against the capacity of the backup media and the time it takes to complete a backup job. These requirements are managed by using different types of jobs in a backup chain. The main types of backups are full only, full with incremental, and full with differential:

- "Full only" means that the backup job produces a file that contains all the data from the source. This means that the backup file is nominally the same size as the source, though it can be reduced via compression. A full backup has the highest storage and time requirements but has the least recovery complexity as only a single file is required.
- "Full with incremental" means that the chain starts with a full backup and then runs incremental jobs that select only new files and files modified since the previous job. An incremental job has the lowest time and storage requirement. However, this type of chain has the most recovery complexity as it can involve two or more jobs, each of which might be stored on different media.
- "Full with differential" means that the chain starts with a full backup and then runs differential jobs that select new files and files modified since the original full job. A differential chain has moderate time and storage requirements and slightly less recovery complexity than incremental as it requires a maximum of two jobs (the full backup plus the differential job).
### Synthetic Backup

A synthetic backup is an option for creating full backups with lower data transfer requirements. A synthetic full backup is not generated directly from the original data but instead assembled from other backup jobs. It works as follows:

1. The chain starts with an initial full backup as normal and subsequently makes a series of incremental backups.
2. When the next full backup is scheduled, the backup software makes one more incremental backup. It then synthesizes a new full backup from the previous full and incremental backups.

### 3-2-1 Backup Rule

The 3-2-1 backup rule is a best-practice maxim that you can apply to your backup procedures to verify that you are implementing a solution that can mitigate the widest possible range of disaster scenarios. It states that you should have three copies of your data (including the production copy), across two media types, with one copy held offline and off site.

### IRP
An incident response plan (IRP) sets out procedures and guidelines for dealing with security incidents. Larger organizations will provide a dedicated Computer Security Incident Response Team (CSIRT) as a single point-of-contact so that a security incident can be reported through the proper channels. The members of this team should be able to provide the range of decision-making and technical skills required to deal with different types of incidents. The team needs managers and technicians who can deal with minor incidents on their own initiative. It also needs senior decision-makers (up to director level) who can authorize actions following the most serious incidents.

### SOPs
- A standard operating procedure (SOP) is a step-by-step list of the actions that must be completed for any given task to comply with policy. Most IT procedures should be governed by SOPs.
-

### ITIL Configuration Management Model

IT Infrastructure Library (ITIL) is a popular documentation of good and best practice activities and processes for delivering IT services. Under ITIL, configuration management is implemented using the following elements:

- Service assets are things, processes, or people who contribute to the delivery of an IT service.
- A configuration item (CI) is an asset that requires specific management procedures for it to be used to deliver the service.
- Configuration baselines are the settings that should be applied to the CI to ensure secure and reliable operation.
- Performance baselines are metrics for expected performance to provide a basis for comparison for ongoing monitoring of a CI.

