# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## DESIGN STEPS:
### Step 1:
Obtain or create a disk image file (e.g., disk.dd) to analyze. Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like mmls, fsstat, and fls to examine the partition layout, file system details, and file listing.

### Step 3:
Interpret the output of the tools to understand the disk structure, including partitions, sectors, and files.
<img width="897" height="623" alt="image" src="https://github.com/user-attachments/assets/1f46c1bb-1a90-4360-9f3b-b32151d87709" />

## PROGRAM:
Sleuth Kit Disk Analysis Commands.
## PROCEDURE:
## ANALYSE THE FILE USING SLEUTHKIT TOOL:

### 1. View File Metadata
  ●	Use istat to view metadata of a file/directory using its inode number 0:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  

  
  #### OUTPUT SUMMARY:
  ●	Type: Directory
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2025-04-14 12:43:12 IST
  
  ●	Size: 2048 bytes, Sectors Used: 31

  
### 2. View Metadata of Inode 1

  ●	Use istat to view metadata of a file/directory using its inode number 1:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  <img width="1115" height="617" alt="image" src="https://github.com/user-attachments/assets/9dbc24a9-cf2f-444a-8ee6-e8a094516e53" />



  #### OUTPUT SUMMARY:
  
  ●	Type: Directory (metasploitable-linux-2.0.0)
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2 2025-03-11 19:34:00 IST
  
  ●	Size: 2048 bytes, Sectors Used: 32
  
### 3. View Metadata of Inode 6

  ●	Use istat to view metadata of a file/directory using its inode number 6:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  


  #### OUTPUT SUMMARY:
  
  ●	File Name: Metasploitable.vmx — This is a VMware configuration.
  
  ●	Type: File — It's a regular file, not a folder.
  
  ●	Permissions: -r-xr-xr-x — Read & execute allowed for everyone, no write access.
  
  ●	Created Time: 2025-03-11 19:34:16 IST — This is when the file was added to the ISO.
  
  ●	Size: 2804 bytes — Small file (just a few KB).
  
  ●	Sectors: 940391, 940392 — The disk sectors storing this file's content.

### 4. Analysis of Inode 6 Metadata via icat Utility

  ●	Use icat to extract file content using its inode number 6:
  
  ●	Command:  icat.exe -f filetype “file path” <inode number>
  
  <img width="1920" height="1080" alt="Screenshot (298)" src="https://github.com/user-attachments/assets/465e2fb9-ea0a-470a-89b3-6efd8addfee4" />


  #### OUTPUT SUMMARY:
  The command retrieves the contents of a VMware virtual machine configuration file (Metasploitable.vmx). This file defines how the virtual machine is set up, including:
  
  ●	Hardware settings like CPU (numvcpus = "1"), RAM (memsize = "512"), and SCSI controller.
  
  ●	Networking options, with both NAT (ethernet0) and Host-only (ethernet1) adapters configured.
  
  ●	Storage devices, such as virtual hard disk (Metasploitable.vmdk) and CD-ROM (auto detect).
  
  ●	Additional devices like USB, EHCI, and multiple PCI bridges.
  
  ●	VM metadata, including UUID, display name (Metasploitable2-Linux), OS type (ubuntu), and annotations.
  
  ●	Security note: The annotation warns that this VM is intentionally vulnerable and should not be exposed to untrusted networks.

### 5. View File System Details Using fsstat
  ●	Use fsstat to view file system metadata of the ISO image.
  
  ●	Command:  fsstat -f filetype “file path”
  <img width="827" height="615" alt="image" src="https://github.com/user-attachments/assets/a89f9af2-f664-461e-9083-16beb786c2dc" />


  <img width="588" height="630" alt="image" src="https://github.com/user-attachments/assets/8fe28ad9-a33e-4ce2-bdf2-8097c196e974" />


  
  #### OUTPUT SUMMARY:
  PRIMARY VOLUME DESCRIPTOR 1 File System Information:
  
  •	File System Type: ISO9660
  
  •	Volume Name: 14_04_2025
  
  •	Volume Set Size: 1
  
  •	Volume Set Sequence: 1
  
  •	Recording Application: AnyBurn
  
  Metadata Information:
  
  •	Path Table Location: 22–22
  
  •	Inode Range: 0 – 9
  
  •	Root Directory Block: 36827386058113052
  
  Content Information:
  
  •	Sector Size: 2048 bytes
  
  •	Block Size: 2048 bytes
  
  •	Total Sector Range: 0 – 940393
  
  •	Total Block Range: 0 – 940393

### 6.List Directory Structure

  ●	Use fls to view directory structure.
  
  ●	Command:  fls -f filetype -r  “file path”
  <img width="766" height="618" alt="image" src="https://github.com/user-attachments/assets/1c52782f-fece-4a75-9600-34809c0b1ab3" />




  #### OUTPUT SUMMARY:
  
  •	Root Directory: metasploitable-linux-2.0.0 (Inode 1)
  
  •	Contained Files and Subdirectories:
  
  o	Metasploitable2-Linux/ — A directory (Inode 2)
  
  o	Metasploitable.nvram — NVRAM file storing BIOS settings (Inode 3)
  
  o	Metasploitable.vmdk — Virtual hard disk file (Inode 4)
  
  o	Metasploitable.vmsd — Snapshot metadata file (Inode 5)
  
  o	Metasploitable.vmx — Main configuration file (Inode 6)
  
  o	Metasploitable.vmxf — Extended configuration file (Inode 7)

### 7. Image File Information

  ●	Use img_stat – Sleuth Kit utility for viewing image file metadata.
  
  ●	Command:  img_stat  “file path”
  


  #### OUTPUT SUMMARY:
  •	Image Type: raw
  
  •	Size in Bytes: 1925926912 (approx. 1.79 GB)
  
  •	Sector Size: 512 bytes
  
  •	Confirms that the input image is a raw format disk image with standard sector configuration.


## RESULT:
Using The Sleuth Kit, the disk structure was successfully analyzed. 

