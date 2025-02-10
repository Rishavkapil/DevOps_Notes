**For Temporary Mounting ->**

1. Create a volume 
2. attach volume to the instance which is in same subnet
3. Connect to local machine 
4. if the volume is not formated then format the volume first
		using mkfs."fileSystem_you_want_to_make" <nameofyourstorege>
		
		**example :**  mkfs.ext4  /dev/xvdf
5 .  Then add a mount point
6 .  then mount the storage to that mount point using 
			mount <nameofyourstorege> <pathtomountpoint>




**For Permanent Mounting ->**

First 6 steps are same as temporary mounting

1 . Next u need to find the UUID of the storage 
2. Now after that add this uuid and storage to /etc/fstab file
	**uuid  /dev/xvdf   /mnt/myvolume   ext4    defaults,nofail   0   2**
	
	/etc/fstab file tells your system how and where to mount storage devices during boot.
UUID is the id of storage block 
/dev/xvdf is the name of the storage
/mnt/myvolume is the mount point where the storage will be accessible in file system
ext4 is the file system type used for the volume 
defaults : These are the mount options that define how the volume should be mounted. Common operations included in defaults are : 
	rw : mount as read -write
	relatime : Optimize access time updates for better performance
	auto : Automatically mount during boot
	exec : Allow executable binaries on the file system
	async : Enable asynchronous i/o operations for better performance.
Nofail  : This ensures that if the volume is missing , the system will not fail to boot.
0 : This field determines whether the volume should be included in file system dumps for backup or not , 0 means no back-up
	And the last field is file system check order .

3. Now again mount all using mount -a


