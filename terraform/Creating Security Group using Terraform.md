

## Terraform dynamic blocks

**Terraform dynamic blocks** are a special Terraform block type that provides the functionality of a **for expression** by creating multiple nested blocks.

The need to create identical (or similar) infrastructure resources is common. A standard use case is multiple virtual server instances on a cloud platform like AWS or Azure Terraform provides routines such as _for_each_and _count_to simplify deploying these resources, removing the requirement for large blocks of duplicate code.

Additionally, teams may need to configure multiple duplicate elements _within_a resource. In conjunction with a _for_each_routine, dynamic blocks are used within an infrastructure resource to remove the need for multiple duplicate "blocks" of Terraform code.


		resource "aws_security_group" "allow_tls" {
		  name        = "allow_tls"
		  description = "Allow TLS inbound traffic"
		  dynamic "ingress" {
		    for_each = [80,8080,443,9090,9000]
		    iterator = port
		    content {
		      description = "TLS from VPC"
		      from_port   = port.value
		      to_port     = port.value
		      protocol    = "tcp"
		      cidr_blocks = ["0.0.0.0/0"]
		    }
		  }
		  egress {
		    from_port        = 0
		    to_port          = 0
		    protocol         = "-1"
		    cidr_blocks      = ["0.0.0.0/0"]
		    ipv6_cidr_blocks = ["::/0"]
		  }
		}


In the above code, we are using a dynamic block to open ports 80,8080,443,9090,9000. you change the values as per your requirement.

now let's modify the instance.tf file, with the below content.


		# creating instance.
		resource "aws_instance" "web" {
		  ami                    = data.aws_ami.ubuntu.id
		  instance_type          = var.instance_type
		  key_name               = aws_key_pair.key-tf.key_name
		  vpc_security_group_ids = ["${aws_security_group.allow_tls.id}"]
		  tags = {
		    Name = "first-tf-instance"
		  }
		  }


