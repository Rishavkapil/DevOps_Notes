

Context are way to define the docker daemon you're interacting with. 

Each context contains all the information required to manage resources on the daemon. The `docker context` command makes it easy to configure these contexts and switch between them. 

syntax : 

		docker context create <context_name>



to switch to other context : 

	docker context use <context_name>


to delete any context , first make sure that you are not in the context that you want to delete

	docker context rm <context_name>



