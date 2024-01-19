
![[Pasted image 20231010163319.png]]PCIe gens

![[Pasted image 20231010164030.png]]

![[Pasted image 20231010164116.png]]

![[Pasted image 20231010164137.png]]

![[Pasted image 20231010164201.png]]There have been numerous versions of SCSI with many different physical connectors, but you are only likely to come across high density (HD) 68-pin connectors or single connector attachment (SCA) 80-pin connectors. SCA incorporates a power connector, while HD-68 is used with Molex power connectors.![[Pasted image 20231010164230.png]]

The **integrated drive electronics (IDE)** interface was the principal mass storage interface for desktop PCs for many years. The interface is also referred to as parallel advanced technology attachment (PATA). The extended IDE (EIDE) bus interface uses 16-bit parallel data transfers.

The **serial** port is a legacy connection interface where data are transmitted over one wire one bit at a time. Start, stop, and parity bits are used to format and verify data transmission. This interface is also referred to as Recommended Standard #232 (RS-232). While modern interfaces like USB are also serial, an RS-232 interface uses much less sophisticated signaling methods. Consequently, an RS-232 serial port supports data rates up to about 115 Kbps only.
![[Pasted image 20231010164500.png]]


![[Pasted image 20231010165506.png]]
### RAID 0 (Striping without Parity)

Disk striping divides data into blocks and spreads the blocks in a fixed order among all the disks in the array. This improves performance as multiple disks are available to service requests in parallel. **RAID 0** requires at least two disks. The logical volume size is the sum of the drives multiplied by the smallest capacity physical disk in the array.

However, RAID 0 provides no redundancy at all. If any physical disk in the array fails, the whole logical volume will fail, causing the computer to crash and requiring data to be recovered from backup. Consequently, RAID 0 only has specialist uses—typically as some type of non-critical cache store.

### RAID 1 (Mirroring)

**RAID 1** is a mirrored drive configuration using two disks. Each write operation is duplicated on the second disk in the set, introducing a small performance overhead. A read operation can use either disk, boosting performance somewhat. This strategy is the simplest way of protecting a single disk against failure. If one disk fails, the other takes over. There is little impact on performance during this, so availability remains good, but the failed disk should be replaced as quickly as possible as there is no longer any redundancy. When the disk is replaced, it must be populated with data from the other disk. Performance while rebuilding is reduced, though RAID 1 is better than other levels in that respect and the rebuilding process is generally shorter than for parity-based RAID.

### RAID 5 (Striping with Distributed Parity)

**RAID 5** uses striping (like RAID 0) but with distributed parity. Distributed parity means that error correction information is spread across all the disks in the array. The data and parity information are managed so that the two are always on different disks. If a single disk fails, enough information is spread across the remaining disks to allow the data to be reconstructed. Stripe sets with parity offer the best performance for read operations. However, when a disk has failed, the read performance is degraded by the need to recover the data using the parity information. Also, all normal write operations suffer reduced performance due to the parity calculation.![[Pasted image 20231010172113.png]]

### RAID 10 (Stripe of Mirrors)

A nested RAID configuration combines features of two basic RAID levels. **RAID 10** is a logical striped volume (RAID 0) configured with two mirrored arrays (RAID 1). This configuration offers excellent fault tolerance, as one disk in each mirror can fail, and the volume will still be available.![[Pasted image 20231010172109.png]]

![[Pasted image 20231010172239.png]]![[Pasted image 20231010172818.png]]
![[Pasted image 20231010184146.png]]
#Core1 