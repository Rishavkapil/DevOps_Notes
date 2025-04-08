

## Step 1 : Power ON -> CPU starts executing 

* When you press the power button , the power is sent to the CPU. 
* The CPU will always start executing code from fixed memory address which maps to BIOS firmware stored in ROM on the motherboard. 



## Step 2 : BIOS Execution 

* BIOS run the POST (Power-ON self test) to check RAM , CPU, keyboard etc. 
* Then it looks for the Boot devices like(HDD , SSD)
* Depending on the system (BIOS or UEFI ), it either 
	* Loads the MBR(for BIOS based system)
	* or loads the EFI file (for UEFI-based systems )


## Step 3 : MBR or EFI Partition 


* In BIOS systems : 
	* The MBR (Master Boot Record) is the first 512 bytes of storage device . 
	* It contains 
		* Bootloader code 
		* Partition table 
	* BIOS Loads this bootloader code into RAM and jumps to it . 
* IN UEFI systems, 
	* There's no MBR , UEFI directly loads the bootloader executable from the EFI partition. 

## Step 4 : Bootloader loads the OS

* Bootloader is now in control 
*  It : 
	* Provides a menu (in multi-OS setups)
	* Loads the kernel into memory 
	* Passes control to OS kernel 