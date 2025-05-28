

Context are way to define the docker daemon you're interacting with. 

syntax : 

		docker context create <context_name>



to switch to other context : 

	docker context use <context_name>


to delete any context , first make sure that you are not in the context that you want to delete

	docker context rm <context_name>



