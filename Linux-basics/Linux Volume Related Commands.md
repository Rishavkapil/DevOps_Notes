All of these commands are used to manage logical volume management (LVM). 

pvcreate : Initializes a disk or partition as a physical volume for use with LVM.
vgcreate : Creates a volume group from one or more physical volumes.
lvcreate : creates a logical volume within a volume group .
vgextend : extending a volume group by adding more physical volume(PV).
lvextend : extends the size of logical volume 
lvreduce : reduce the size of logical volume
lvremove : removes a logical volume permanently 
vgremove : removes a volume group 
pvremove : removes LVM metadata from a physical volume , making it a regular disk.