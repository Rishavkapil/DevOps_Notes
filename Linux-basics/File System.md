**File System :** File system is a logical and physical system for organizing , managing and accessing files.

Without a file system , the operating system OS would see only large chunks of data without any way to distinguish one file from another. 

Along with a file's content data, a file system maintains [metadata](https://www.techtarget.com/whatis/definition/metadata) about the files along with other information. The metadata might include details such as the file size, creation date or location in the directory.


A file system divides a partition  into blocks and their sizes depend on the file system itself. 

![[Pasted image 20250122105154.png]]

**Super Block :** The block contains information about the file system itself. Its like meta data for file system.eg. type, total no. of blocks etc.
**Data Block Bitmap :** The block contains a simple bitmap that indicates which data blocks are used or unused. 1 means inode is used and 0 means inode is unused.
		**What is inode ?** [An inode](http://www.linfo.org/inode.html) is a file data structure that stores information about any Linux file except its name and data.
				**Where inodes get more complex ?**
						Much like your fixed-size blocks of data, inodes are also uniform. It is possible that you have a file that exceeds the size of your inode. In this case, your original inode will have to point to _another_ inode in order to fully encompass the file’s metadata. This is called an **indirect pointer**.
		**Data Block :**  These are the storage units where actual content of the file is stored.
		**INodes :** inode is short name for Index nodes. store metadata about file and directory. 
**Inode bitmap :**  The block contains a simple bitmap that indicates which inodes are used or unused. A value of 1 indicates the inode is used, and a value of 0 indicates it is unused.


**Types of file system :** 
1. FAT(File allocation Table)
2. Extended File Allocation Table (exFAT)
3. New Technology File System (NTFS)
4. Resilient File system(RFS)
5. Extended File System (EXT) : The current version, ext4, builds on ext3, which added journaling capabilities to reduce data corruption.The ext4 version provides better performance and reliability while supporting greater scalability.