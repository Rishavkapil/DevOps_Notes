
If you don't create any Parameter group , the default parameter group will be created and once the default parameter group is created you cannot modify the default parameter group . 



**To create a custom Parameter group :** 

- choose create Parameter group 
- give description
- choose engine type 
- choose parameter group family(make sure that i matches the version of the DB engine)
- choose Type of the parameter group (e.g cluster or for single instance)



![[Pasted image 20250318130933.png]]



Then click create 
and if you want to modify the parameters of the Group. 

Click On the parameter group that you want to edit ,
then click on Actions -> then Edit -> then change the configuration or rule e.g max_connections = 2 or read_only =0 
![[Pasted image 20250318131143.png]]


***NOTE :  If you limit the connections to 1 , and tried to connect your ec2 instance , it will not happen because RDS has some pre-defined connections for its own tasks like monitoring , etc.***



