
# What is the function of /dev directory ?

The /dev directory consist of files that represent devices that are attached to the local system . However , these are not regular files that user can read and write to; these files are called device files or special files. 


```
[root@localhost dev] ls -l
total 0
crw-r--r--. 1 root root     10, 235 Sep 29 12:08 autofs
drwxr-xr-x. 3 root root          60 Sep 29 12:07 bus
lrwxrwxrwx. 1 root root           3 Sep 29 12:10 cdrom -> sr0
drwxr-xr-x. 2 root root        3100 Sep 29 12:10 char
crw-------. 1 root root      5,   1 Sep 29 12:08 console
lrwxrwxrwx. 1 root root          11 Sep 29 12:07 core -> /proc/kcore
drwxr-xr-x. 3 root root          60 Sep 29 12:07 cpu
crw-------. 1 root root     10,  62 Sep 29 12:08 cpu_dma_latency
drwxr-xr-x. 7 root root         140 Sep 29 12:08 disk
brw-rw----. 1 root disk    253,   0 Sep 29 12:08 dm-0
```

### What is the difference between character special files and block special files 

Character special files are simple interfaces to character devices, Likewise block special files are simple interfaces to block devices. The difference between these devices depends on how the operating system reads data off of them. 

**Character Special files** : 
* Data is transferred character by character(byte stream).
* They do not buffer data -> transfer happens immediately. 
* Suitable for devices that send/receive data in a continues stream. 
Example: 
* Keyboard(/dev/tty) -> every stroke is sent directly.
* Serial ports
They allow direct I/O without intermediate storage. 


 **Block Special files :** 

- Data is transferred in blocks(chunks, usually 512 bytes or more)
- They use buffering and caching to optimize I/O. 
- Suitable for devices that can store and retrieve data in fixed-size blocks. 

Example: 
* Hard disks (/dev/sda)
* USB drivers

They allow random access(read/write any block without reading sequentially)

