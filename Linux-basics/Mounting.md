Mounting is the process of making file system , such as hard disk partition, USB drive or network storage etc. accessible within the file system hierarchy.

like if we have purchased a secondary memory and we want to store something in it. Then we need some gateway to access that memory and to store in that memory. For that, we mount the memory to any directory and whatever changes we do in that directory like making new files,folders etc. and this process is called **mounting.**
The directory on which storage is mounted is called **Mount Point.** 

**Mounting is of two types :** 
- **Temporary Mounting** : Storage gets unmounted when computer is restarted or reboot.
- **Permanent Mounting** : Storage gets permanently mounted to a directory. it uses /etc/fstab

**Common commands :** 
mount : used to attach file systems.
unmount: used to detach file systems.

Example :  sudo mount /dev/sdb1   mnt/usb

		here /dev/sdb1 is the storage device 
			and mnt/usb is the mount point or the directory in which storage is  
			to be mounted.
	