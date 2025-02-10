NFS is a mechanism for storing files or directories on a network.
An NFS server is a machine or device that shares its files or directories with other devices over the network.x

**How to connect 2 instances using nfs server :** 

1. Create a volume to attach to server side
2. make a directory in server side which you want to mount to client side
3. install nfs server using 
				
				sudo apt-get update

			sudo apt install nfs-kernel-server
4. Change the permissions of that to 777 so that eveyone can modify that file or directory
5. Define access for nfs client in Export file
			edit  /etc/exports file and add one of three of following : 
		
	**To enable access to a single client**

		/mnt/myshareddir {clientIP}(rw,sync,no_subtree_check)
	
**To enable access to several clients**

	/mnt/myshareddir {clientIP-1}(rw,sync,no_subtree_check)

	{clientIP-2}(...)
	
	{clientIP-3}(...)

**To enable access to an entire subnet**

	/mnt/myshareddir {subnetIP}/{subnetMask}(rw,sync,no_subtree_check)


6.   Make the NFS Share Available to Clients: 
			You can now make the shared directory available to clients using the exportfs command.
			
			sudo exportfs -a #making the file share available  
			sudo systemctl restart nfs-kernel-server #restarting the NFS kernel


##  Setting Up NFS on Client Machine and Mounting an NFS Share

### Installing NFS Client Packages
			sudo apt update  
			sudo apt install nfs-common

### Mounting the NFS File Share Temporarily

1. You can mount the NFS folder to a specific location on the local machine, known as a mount point,
		1. Create a local directory—this will be the mount point for the NFS share. In our example we’ll call the folder /var/locally-mounted.

					sudo mkdir /var/locally-mounted


2. Mount the file share by running the mount command, as follows. There is no output if the command is successful.

			sudo mount -t nfs {IP of NFS server}:{folder path on server} /var/locally-mounted

