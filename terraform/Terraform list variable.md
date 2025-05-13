
List in terraform is like a array or vector in programming languages. 

A **List variable**  holds a list of variables (for example , name of users) to be used . Each list variable specifies the order . 

				variable users {
					type = list 
				}


Lets create one more file that will access users from users variable. 

		output printlist {
			value = "first user is ${var.users[0]}"
		}


