
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
