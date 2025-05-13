


output "firstBlock" {
	value = "Hello from first block"
}
output "secondBock" {
	value = "Hello from Second Block "
}
output "thirdBlock" {
	value = "Hello from third Block "
}

But the problem with this is , if we have to create 100s resources , then we need to make very very large files which would be very complex to manage . 

So to handle this , we destructure this 

we create multiple terraform files in one directory 