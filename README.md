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

✅ Option 1: Create a Sample Disk Image (for Testing)

Let’s create a 10MB blank disk image and simulate file system activity:

```bash
cd ~/Downloads

# Step 1: Create an empty disk image
dd if=/dev/zero of=disk.dd bs=1M count=10

# Step 2: Format it with a file system (like FAT32)
mkfs.vfat disk.dd
```

## OUTPUT:

![Screenshot 2025-04-22 085615](https://github.com/user-attachments/assets/48ad4510-e6d3-42cc-a6f7-a5453af7e6a9)

### Create Disk

![image](https://github.com/user-attachments/assets/486b446a-0c92-4841-a095-3980000c3fc8)
### mmls 
```bash
mmls disk.dd
```
### fls
```bash
fls -f fat -o 0 disk.dd
```
![image](https://github.com/user-attachments/assets/85967a1e-38ab-4281-aa16-820b2cfa7479)

![image](https://github.com/user-attachments/assets/36499cfc-15f3-4b86-8023-7876a2d5df25)


![image](https://github.com/user-attachments/assets/1972eea0-f2aa-471e-8cc7-83e1279f38eb)

![image](https://github.com/user-attachments/assets/2f3834c6-b0da-45d9-a207-c1afc7937b3c)

## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
