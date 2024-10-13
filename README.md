# windows-server
Everything Windiws Server - [Trainer Handbook with Hands on and Slides SS on right side](https://koenigsolutionsltd-my.sharepoint.com/:b:/g/personal/ananay_ojha_koenig-solutions_com/EarRBhcgTVZIqfgctPGSARkBViK70Ks1WTWW-KDMYeaT-g?e=PKOC2E)

# Links
1. install windows server core (means no gui) - https://learn.microsoft.com/en-us/windows-server/administration/server-core/what-is-server-core
2. server vs datacentre edition - https://learn.microsoft.com/en-us/windows-server/get-started/editions-comparison?pivots=windows-server-2016

### MOd-2: Storage

## Basics:
> MBR and GPT manage how a disk is structured, while file systems like FAT32 and exFAT manage how data is organized within those structures. Understanding these concepts helps you optimize your storage for better performance and compatibility with your devices.

1. [Create and format a hard disk partition](https://support.microsoft.com/en-us/windows/create-and-format-a-hard-disk-partition-bbb8e185-1bda-ecd1-3465-c9728f7d7d2e)
2. these things possible - [docs](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/overview-of-disk-management):
> Master Boot Record (MBR) disks use the standard BIOS partition table. GUID partition table (GPT) disks use the Unified Extensible Firmware Interface (UEFI). One advantage of GPT disks is that you can have more than four partitions on each disk. GPT is also required for disks larger than 2 terabytes (TB).
- Manage disks
- Initialize new disks
- Move disks to another computer
- Change a dynamic disk back to a basic disk
- Convert an MBR disk into a GPT disk
- Convert a GPT disk into an MBR disk
- Manage Virtual Hard Disks
3. [Overview of FAT, HPFS, and NTFS File Systems](https://learn.microsoft.com/en-us/troubleshoot/windows-client/backup-and-storage/fat-hpfs-and-ntfs-file-systems)

# GPT:
It might seem like all file systems are the same at a glance since they all present folders and files in a hierarchy. However, the differences between file systems like NTFS, ReFS, and FAT can significantly affect performance, features, and data management. Here’s a breakdown:

# 👍✅💡 What is a File System?

A file system is the way an operating system organizes and manages files on a storage device. It defines how data is stored, accessed, and retrieved. Each file system has its own set of rules and features.

### Key Differences and Features

1. **Storage Capacity and File Size Limits:**
   - **FAT32:** Maximum file size of 4 GB and a maximum partition size of 8 TB. Good for compatibility but limited for large files.
   - **NTFS:** Supports much larger files (up to 16 TB in some implementations) and partitions, making it suitable for modern usage.
   - **ReFS (Resilient File System):** Designed for high availability and large data volumes, supporting very large file sizes and storage pools.

2. **Performance:**
   - **NTFS:** Offers better performance for large files and supports features like compression and encryption, which can enhance speed and security.
   - **FAT32:** Simpler and faster for small files but can slow down with many files or large partitions.

3. **Data Integrity and Recovery:**
   - **NTFS:** Has journaling features that help prevent data loss by keeping track of changes before they are made, making it easier to recover from crashes.
   - **ReFS:** Also uses a form of journaling and is designed to resist data corruption, making it ideal for critical applications.
   - **FAT32:** Lacks these features, making it more prone to data loss and corruption.

4. **Permissions and Security:**
   - **NTFS:** Supports file permissions and encryption, allowing for better security and user access control.
   - **ReFS:** Designed for enterprise environments with advanced data integrity features but doesn’t support traditional NTFS permissions.
   - **FAT32:** Offers no permissions or encryption, making it less secure.

5. **Use Cases:**
   - **FAT32:** Often used for USB drives and external storage due to its broad compatibility across devices.
   - **NTFS:** Typically used for Windows system drives and large internal drives due to its advanced features.
   - **ReFS:** Mainly used in server environments and for specific applications where data integrity and availability are crucial.

### Why It Matters

While you may not notice a difference in basic file management, the underlying file system affects:

- **Performance:** Speed and efficiency in handling files.
- **Reliability:** How well your data is protected against loss or corruption.
- **Compatibility:** Whether you can use your drive across different operating systems and devices.

Choosing the right file system based on your needs can enhance your experience, especially for tasks involving large files, security, or critical data management.

# 💡✅👍 Why Partitions Matter

1. **Organization:** Without partitions, everything would be stored in one continuous space, making it harder to manage data. Partitions allow you to separate system files from personal files, backups, etc.

2. **Multiple Operating Systems:** If you want to run more than one operating system (like Windows and Linux), partitions let you keep them separate without conflicts.

3. **Data Integrity:** Partitions can help contain issues like file system corruption. If one partition fails, others might remain intact.

### UEFI and Bootloaders

1. **UEFI (Unified Extensible Firmware Interface):** This is a modern replacement for BIOS. It manages the booting process of your computer and interacts with the operating system.

2. **Bootloader:** The bootloader is software that loads the operating system. With UEFI, you can boot from drives formatted with GPT and take advantage of features like secure boot.

### What If You Have No Partitions?

- **Single Partition:** It is possible to have a single partition covering the entire disk, which is common for certain setups. However, this limits flexibility and organization.
  
- **Impact on Booting:** Without partitions, you usually can't have multiple operating systems. Additionally, booting from a single partition can complicate recovery and backups.

### Summary

While technically you could function without partitions, they provide significant advantages in organization, management, and functionality. UEFI and bootloaders facilitate modern booting processes and make it easier to manage how your system starts and interacts with storage. In short, they help create a smoother, more organized user experience!

Sure! Here are the key points about a striped set without parity or mirroring in RAID (RAID 0), presented like a training session:

### 👍✅💡 Key Points of RAID 0 (Striped Set Without Parity or Mirroring)
- [Article on RAID](https://www.easeus.com/storage-media-recovery/raid-5.html)

1. **Definition:**
   - **Striping:** Data is divided into blocks and distributed across multiple drives.

2. **Performance Boost:**
   - **Increased Speed:** Allows simultaneous read/write operations, enhancing performance. 
   - **Real-Life Example:** Think of a highway with multiple lanes (drives); more lanes allow more cars (data) to travel simultaneously, speeding up traffic.

3. **Full Capacity Utilization:**
   - **Storage Efficiency:** Total capacity equals the sum of all drives. 
   - **Real-Life Example:** If you have two 1 TB drives in RAID 0, you get 2 TB of usable space (no space wasted on redundancy).

4. **No Redundancy:**
   - **Data Risk:** If one drive fails, all data in the array is lost.
   - **Real-Life Example:** Imagine storing all your important documents in a single box; if the box gets lost or damaged, you lose everything inside.

5. **Increased Failure Risk:**
   - **Higher Probability:** More drives mean a higher chance of failure.
   - **Real-Life Example:** The more eggs you put in one basket, the more likely you are to break them if the basket falls.

6. **Use Cases:**
   - **Ideal for Performance-Driven Tasks:** Great for gaming, video editing, or applications requiring fast data access.
   - **Real-Life Example:** A sports car (RAID 0) excels on the racetrack (high-speed tasks) but lacks a spare tire (no redundancy).

### Summary
RAID 0 is all about speed and capacity but comes with a significant risk of data loss due to the lack of redundancy. It’s perfect for scenarios where performance is the priority, but always consider backups to protect against failures!

Sure! Let’s break down DAS, NAS, SAN, and file servers into key points, highlighting their differences with real-life examples:

# 💡✅👍 DAS vs NAS vs File Server

#### 1. **Direct Attached Storage (DAS)**
- **Definition:** Storage directly connected to a single computer or server (e.g., external hard drives).
- **Accessibility:** Only the connected device can access the storage.
- **Real-Life Example:** A USB drive plugged into your laptop—only your laptop can use it.

#### 2. **Network Attached Storage (NAS)**
- **Definition:** A dedicated storage device connected to a network, allowing multiple users and devices to access it.
- **Accessibility:** Accessible by any device on the same network (e.g., PCs, smartphones).
- **Real-Life Example:** A shared family photo library on a NAS device, allowing all family members to upload and view photos from their devices.

#### 3. **Storage Area Network (SAN)**
- **Definition:** A high-speed network specifically designed to connect storage devices to servers, providing block-level storage.
- **Accessibility:** Enables multiple servers to access shared storage, often used in enterprise environments.
- **Real-Life Example:** A data center where multiple servers (like virtual machines) access a pool of shared storage devices, similar to a multi-lane highway connecting various buildings.

#### 4. **File Server**
- **Definition:** A server dedicated to storing and managing files, allowing multiple users to access shared files over a network.
- **Accessibility:** Provides file-level access to users on the network, often part of a NAS or a dedicated server.
- **Real-Life Example:** An office server where all employees can access, edit, and save documents, similar to a library where everyone can borrow and return books.

### Summary
- **DAS:** Direct, individual use—like a personal backpack.
- **NAS:** Shared storage for a network—like a family closet.
- **SAN:** High-performance storage network—like a highway system for data.
- **File Server:** Manages files for network users—like a public library for documents.

Yes, you can mount DAS, NAS, SAN, and file servers as drives on your system, allowing you to access them like any local storage. Here’s a quick overview:

### Mounting Options

1. **Direct Attached Storage (DAS):**
   - **How to Mount:** Simply connect the storage device (e.g., USB drive) to your computer. It usually mounts automatically and appears as a local drive.

2. **Network Attached Storage (NAS):**
   - **How to Mount:** You can map a NAS share to a drive letter in your operating system (e.g., Windows or macOS). It appears as a network drive, accessible like a local drive.
   - **Example:** You access it through the network path (e.g., `\\NAS_Device\SharedFolder`).

3. **Storage Area Network (SAN):**
   - **How to Mount:** SAN storage is typically presented to servers as block storage, which can be formatted and mounted as local drives. This requires specific configurations, often done in enterprise environments.
   - **Example:** A SAN may show up as additional disks in the server’s disk management utility.

4. **File Server:**
   - **How to Mount:** Similar to NAS, you can map shared folders from a file server to a drive letter on your system.
   - **Example:** Access files through a network path (e.g., `\\FileServer\SharedDocuments`).

### Summary
While all these storage types can be mounted as drives, the method of access and the underlying technology differ. DAS is local, while NAS, SAN, and file servers rely on network connectivity, each serving distinct use cases based on performance and accessibility needs.

Connection: DAS is an external storage option, while the C drive is internal and essential for the OS.
Function: DAS provides extra storage or backups, while the C drive is where the operating system and primary applications reside.
Accessibility: Both are accessible only by the computer they are connected to, but DAS can be moved between systems easily.
