
File System is a method used by operating system to store, retrieve and manage data on storage devices (like hard disks , SSDs etc. )

Think of it like a library system : 

*  The Bookshelves (directories ) helps organize books(files)
* You need a cataloging method( file system ) to know where each book is placed. 



#### Key parts of Linux File System

Linux treats everthing as file - including directories , hardware devices , and even processes. 

##### The Root Directory (/); 

*  The top level directory in Linux 
* All other files and directories are children of /

			/
			├── bin        # Essential binary programs (like ls, cp)
			├── boot       # Boot loader files (e.g., kernel)
			├── dev        # Device files (e.g., /dev/sda)
			├── etc        # System config files
			├── home       # User home directories
			├── lib        # Essential shared libraries
			├── media      # External devices (USB, CD)
			├── opt        # Optional software
			├── proc       # Virtual filesystem (processes info)
			├── root       # Home directory of root user
			├── sbin       # System binaries (like shutdown)
			├── tmp        # Temporary files
			├── usr        # User utilities and applications
			├── var        # Variable data (logs, mail, etc.)


### File System Types (Format)


Just like windows has NTFS or FAT32 , Linux supports multiple file systems. Common ones include : 

ext4 
xfs : Good for large files and scalability 
btrfs : Advanced supports snapshots and compression


### Important file system Commands 


##### Checking file system
`df -h` : shows disk free in human readable format 

`du -sh /path`  : shows size of a directory 

`lsblk `: List block devices 


##### Mounting file system 

		mount /dev/sbd1 /mnt 
		unmount /mnt


##### File System Creation 

		mkfs.ext4 /dev/sbd1


#### Other Important Concepts 

1.  **Inodes**
		- Each file has inode which stores metadata. 
		- To see inode info : 
			- ls -i

2. **Mount Points**
		- Linux uses a single directory tree,
		- Devices are mounted to directories (mount points ) to become accessible 
		- You can mount a new disk under /data , /mnt etc. 

3. **Symbolic VS Hard Links :** 
		- Hard Link : Points directly to the inode
		- Soft Link : Points to the file path 


4. **fstab:**
		File : /etc/fstab
		Defines file system to be mounted at boot. 
		Example : /dev/sbd1        /data       ext4       defaults       0        0 

