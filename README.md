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

## PROGRAM:
Sleuth Kit Disk Analysis Commands
## PRELIMINARY STEP:
### Step1:

  ●	Run command prompt as administrator
![image](https://github.com/user-attachments/assets/88d50e21-5d20-4d07-a8c4-3635496388a1)

### Step2:

  ●	Verify Sleuthkit is installed.
  ![image](https://github.com/user-attachments/assets/504edd66-9700-490f-b6c5-878d5ccba681)

### Step3:

  ●	Navigate to the binary file of Sleuthkit in command prompt: 
  ![image](https://github.com/user-attachments/assets/5e792732-51f0-4b7f-b299-cc21699104e8)

## PROCEDURE:
## ANALYSE THE FILE USING SLEUTHKIT TOOL:

### 1. View File Metadata
  ●	Use istat to view metadata of a file/directory using its inode number 0:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  <img width="1920" height="1080" alt="Screenshot (294)" src="https://github.com/user-attachments/assets/ab487752-7bf3-41c8-8473-decb5f04e9a1" />

  
  #### OUTPUT SUMMARY:
  ●	Type: Directory
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2025-04-14 12:43:12 IST
  
  ●	Size: 2048 bytes, Sectors Used: 31

  
### 2. View Metadata of Inode 1

  ●	Use istat to view metadata of a file/directory using its inode number 1:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  <img width="1920" height="1080" alt="Screenshot (297)" src="https://github.com/user-attachments/assets/5060f8d8-b912-4922-b7c0-040333e6f7ae" />


  #### OUTPUT SUMMARY:
  
  ●	Type: Directory (metasploitable-linux-2.0.0)
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2 2025-03-11 19:34:00 IST
  
  ●	Size: 2048 bytes, Sectors Used: 32
  
### 3. View Metadata of Inode 6

  ●	Use istat to view metadata of a file/directory using its inode number 6:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  <img width="1920" height="1080" alt="Screenshot (298)" src="https://github.com/user-attachments/assets/86f8d5d0-c47f-4c27-8f0c-81d4c00cec8a" />


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
  <img width="1920" height="1080" alt="Screenshot (299)" src="https://github.com/user-attachments/assets/48bebd99-3cc1-4209-9f79-74dae1dd269a" />

  <img width="1920" height="1080" alt="Screenshot (300)" src="https://github.com/user-attachments/assets/af7cc3cf-f938-4b43-88a7-bb299f5945ad" />

  
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
  <img width="1920" height="1080" alt="Screenshot (301)" src="https://github.com/user-attachments/assets/ea772cdc-6863-4a6a-9e58-be83b4472ff6" />



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
  <img width="1920" height="1080" alt="Screenshot (302)" src="https://github.com/user-attachments/assets/7099fd19-9745-4a2a-8433-6d6cebd40846" />


  #### OUTPUT SUMMARY:
  •	Image Type: raw
  
  •	Size in Bytes: 1925926912 (approx. 1.79 GB)
  
  •	Sector Size: 512 bytes
  
  •	Confirms that the input image is a raw format disk image with standard sector configuration.


## RESULT:
Using The Sleuth Kit, the disk structure was successfully analyzed. 

