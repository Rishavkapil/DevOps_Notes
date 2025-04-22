

Finalizers in kubernetes are like "cleanup hooks " that let you tell kubernets : 

"Wait !  Don't delete this resource yet - I have some cleanups to do first..." 

when you delete a kubernetes objects (like a pod or namespace, ) it doesn't always get deleted right away. 
If the object has finalizers , kubernetes will wait until those finalizers are removed. 



## How finalizers work 

When you create a resource using the manifest file, you can specify finalizers in the `metadata.finalrizers` feild. 

When you attempt to delete the resource , the API server handling delete requests notices the values in the finalizers field and does the following : 

- Modifies the object to add a `metadata.deletionTimestamp` field with the time you started the deletion.

- Prevents the object from being removed until all items are removed from its `metadata.finalizers` field

- Returns a `202` status code (HTTP "Accepted")