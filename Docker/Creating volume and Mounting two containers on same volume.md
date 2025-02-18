
###  step 1 : Create a  volume 


			docker volume create <volume_name>



#### Step 2 : Run the first Container and Mount the volume 

	
			docker run -dit --name container1 -v <volume_name>: /data ubuntu



#### Step 3 : Run the second Container and Mount the volume



		docker run -dit --name container2 -v <volume_name>: /data ubuntu




#### Step 4 : Verify that both can access the shared volume



	docker exec -it container1 bash
	echo "Hello from Container1 ">/data/shared_file.txt
	exit


	docker exec -it container2 bash
	cat /data/shared_file.txt


If the output is **`Hello from Container1`** , then volume is successfully shared between two containers




