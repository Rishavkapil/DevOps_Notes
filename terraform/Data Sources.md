
Data sources allow Terraform to use the information defined outside of Terraform, defined by another separate Terraform configuration, or modified by functions.

A data source is accessed via a special kind of resource known as a _data resource_, declared using a data block.

```sh
data "aws_ami" "example" {
  most_recent = trueowners = ["self"]
  tags = {
    Name   = "app-server"Tested = "true"
  }
}
```


	A data block requests that Terraform read from a given data source `aws_ami` and export the result under the given local name `example`. The name is used to refer to this resource from elsewhere in the same Terraform module, but has no significance outside of the scope of a module.

The data source and name together serve as an identifier for a given resource and so must be unique within a module.

Within the block body (between { and }) are query constraints defined by the data source. Most arguments in this section depend on the data source, and indeed in this example most_recent, owners and tags are all arguments defined specifically for the aws_ami data source.

When distinguishing from data resources, the primary kind of resource (as declared by a resource block) is known as a _managed resource_. Both kinds of resources take arguments and export attributes for use in configuration, but while managed resources cause Terraform to create, update, and delete infrastructure objects, data resources cause Terraform only to _read_ objects. For brevity, managed resources are often referred to just as **resources** when the meaning is clear from context.

now let's modify our code to use data sources.

modify terraform.tfvars files with the below content


```sh
ports         = [22, 80, 443, 3306, 27017, 1080]
instance_type = "t2.micro"
image_name    = "ubuntu/images/hvm-ssd/ubuntu-focal-20.04-amd64-server-*"
```



now modify the instance.tf file.


```sh
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"]
  filter {
    name   = "name"
    values = ["${var.image_name}"]
  }
  filter {
    name   = "root-device-type"
    values = ["ebs"]
  }
  filter {
    name   = "virtualization-type"
    values = ["hvm"]
  }
}


# creating instance.
resource "aws_instance" "web" {
  ami                    = data.aws_ami.ubuntu.id
  instance_type          = var.instance_type
  key_name               = aws_key_pair.key-tf.key_name
  vpc_security_group_ids = ["${aws_security_group.allow_tls.id}"]
  tags = {
    Name = "first-tf-instance"
  }
  user_data = file("${path.module}/script.sh")
  connection {
    type        = "ssh"
    user        = "ubuntu"
    private_key = file("${path.module}/id_rsa")
    host        = self.public_ip
  }
  # file, local-exec, remote-exec
  provisioner "file" {
    source      = "readme.md"      # terraform machine
    destination = "/tmp/readme.md" # remote machine
  }
  provisioner "file" {
    content     = "this is test content" # terraform machine
    destination = "/tmp/content.md"      # remote machine
  }
  provisioner "local-exec" {
    command = "env>env.txt"
    environment = {
      envname = "envvalue"
    }
  }
  provisioner "local-exec" {
    command = "echo 'at Create'"
  }
  provisioner "local-exec" {
    when    = destroy
    command = "echo 'at delete'"
  }
  provisioner "remote-exec" {
    inline = [
      "ifconfig > /tmp/ifconfig.output",
      "echo 'hello gaurav'>/tmp/test.txt"
    ]
  }
  provisioner "remote-exec" {
    script = "./testscript.sh"
  }
}
```

kindly notice we replace image_id with data source value.