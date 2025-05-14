
The terraform language include number of built in functions that you can call from within expressions to transform and combine values . The general syntax for function calls is a function name followed by comma-seperated arguments in the parenthesis. 

eg. 

	max(5,12,3)

	or join(",",["foo","bar","zee"])

output : foo , bar , zee



For example : 


			output printOutput{
				value = "${upper(var.users[0])}"
			}
			output printoutput{
				value = "${title(var.users[0])}"
			}



